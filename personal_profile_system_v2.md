# Personal Profile System v2.0 — Specification

> **Purpose**
>
> A robust, consistent, and extensible system for maintaining a long-term personal profile with ChatGPT, using:
> - layered memory architecture  
> - a deterministic delta-extraction engine (CMDF)  
> - a command-based interface (CMDF-CLI)  
> - a strict standard output format (CMDF-SOF)  
> - full-conversation scanning and knowledge-confidence modeling  

This document is designed to be **implementation-agnostic**: it can be realized in Markdown, JSON, Python, or any other language/tooling.

---

## 1. High-Level Architecture

The Personal Profile System v2.0 has **three memory layers**:

1. **Core Profile (Layer A)**  
   - Stable, evergreen identity and traits.
   - Slowly changing over time.
   - Includes identity, cognition style, core skills, devices, automotive info, etc.

2. **CMDF Memory (Layer B)**  
   - Dynamic, extracted deltas from conversations.
   - Captures new or refined skills, projects, preferences, behavioral patterns.
   - Produced exclusively by the **CMDF pipeline**.

3. **External Archive (Layer C)** *(optional but recommended)*  
   - Historical logs, exported conversations, snapshots.
   - Used as input for CMDF but not stored directly in core memory.

All updates to long-term memory should go through **CMDF** for consistency and noise reduction.

---

## 2. Core Profile Structure (Layer A)

The core profile is a **single canonical object** describing the person at a high level.

### 2.1 Example Core Profile Schema (Conceptual)

```jsonc
{
  "identity": {
    "name": "Connor Cieslinski",
    "timezone": "America/Denver",
    "consent_for_memory": true
  },
  "health": {
    "ocd": true,
    "trigger_safety_rules": "avoid alarmist biological/electrical framing"
  },
  "cognition_style": {
    "analytical": true,
    "mechanistic_reasoning": true,
    "low_uncertainty_tolerance": true,
    "optimization_tendency": true,
    "direct_communication": true,
    "stepwise_explanations": true,
    "low_fluff_preference": true,
    "iterative_debugging": true,
    "meta_cognition_level": "high"
  },
  "emotional_patterns": {
    "defensiveness": "low",
    "learning_drive": "high",
    "uncertainty_anxiety": "medium_high",
    "curiosity_driven_focus": "high"
  },
  "communication_style": {
    "direct": true,
    "detail_rich": true,
    "concise_when_possible": true,
    "prefers_models_over_metaphors": true,
    "requests_mechanistic_breakdowns": true
  },
  "reasoning_style": {
    "hardware_first_thinking": true,
    "abstraction_tolerance": "low",
    "prefers_visible_state": true,
    "determinism_priority": true,
    "instruction_cycle_awareness": true
  },
  "creative_domains": {
    "audio_synthesis": true,
    "daw_development": true,
    "dsp_experimentation": true,
    "ui_framework_design": true,
    "waveform_visualization": true,
    "parametric_eq_design": true
  },
  "preferences": {
    "low_abstraction_code": true,
    "explicit_register_management": true,
    "deterministic_systems": true,
    "real_time_visualizations": true,
    "minimal_dependencies": true,
    "hands_on_learning": true
  },
  "technical_domains": {
    "embedded_systems": [
      "STM32",
      "USART",
      "ADC",
      "GPIO",
      "internal_temp_sensor"
    ],
    "shift_registers": ["74HC595"],
    "sram": ["MCM6064P12", "HM1-6514-5"],
    "assembly_languages": ["Z80", "ARM"],
    "c_programming": true,
    "hardware_debugging": true,
    "timing_analysis": true,
    "software": {
      "languages": ["C", "Assembly", "Shell", "Java", "XML"],
      "web_audio": true,
      "convolution_reverb": true,
      "oscillators": true,
      "parametric_eq": true,
      "gpu_compute_experiments": true
    },
    "systems_networking": {
      "dns": true,
      "nslookup_discrepancies": true,
      "vps_usage": true,
      "vpn_issues": true,
      "port_restrictions": true,
      "firewalls": ["ufw"],
      "pterodactyl_wings": true,
      "mysql_on_wsl": true
    },
    "os_and_toolchains": {
      "fuzix_pico_build": true,
      "keil": true,
      "cubeide": true,
      "gcc_ld": true,
      "linux_cli": true
    }
  },
  "projects": {
    "daw_synth": {
      "long_term": true,
      "components": [
        "oscillators",
        "visualizers",
        "import_export",
        "midi",
        "reverb",
        "panner"
      ]
    },
    "parametric_eq": {
      "long_term": true,
      "features": [
        "real_time_curve",
        "multi_band",
        "drag_points",
        "biquads"
      ]
    },
    "waveform_extraction": true,
    "retrocomputing_z80_systems": true,
    "fuzix_pico_driver_development": true,
    "bios_modding_nvme_ga970a": {
      "status": "archived_but_reference"
    },
    "catalystui_framework": true
  },
  "development_style": {
    "low_abstraction": true,
    "visible_state": true,
    "deterministic_behavior": true,
    "performance_bias_predictable": true,
    "heavy_debug_iteration": true,
    "code_patterns": {
      "python": {
        "procedural": true,
        "minimal_dependencies": true,
        "direct_loops": true
      },
      "arduino_cpp": {
        "direct_registers": true,
        "global_state_ok": true,
        "simple_control_flow": true
      },
      "assembly": {
        "tight_loops": true,
        "cycle_counting": true,
        "explicit_labels": true
      }
    }
  },
  "devices": {
    "desktop": {
      "cpu": "Ryzen 5 3600X",
      "gpu": "GTX 1080",
      "ram": "28GB DDR4 mixed",
      "storage": ["512GB NVMe", "2TB SSD"]
    },
    "laptop_primary": {
      "model": "Lenovo IdeaPad 81XH",
      "cpu": "i7-10510U"
    },
    "laptop_server": {
      "model": "Acer Swift SF-314-54",
      "cpu": "i5-8250U"
    }
  },
  "automotive": {
    "vehicle": "1995 Mitsubishi Mirage LS coupe",
    "engine": "1.8L",
    "transmission": "Manual",
    "experience": ["clutch diagnosis", "synchro issues"]
  },
  "gaming": {
    "minecraft_modded": true,
    "geometry_dash": true,
    "rocket_league": {
      "ranks": {
        "duel_1v1": "Gold II",
        "doubles_2v2": "Gold II/III",
        "standard_3v3": "Platinum III",
        "tournament": "Diamond II"
      },
      "mechanics_known": ["speed_flip", "half_flip"]
    },
    "subnautica": true,
    "valheim": true,
    "terraria": true,
    "obs_discord_camo_studio_usage": true
  },
  "memory_system": {
    "cmdf_version": "1.0+full_scan",
    "cmdf_cli_enabled": true,
    "cmdf_sof_schema_enabled": true,
    "knowledge_confidence_tokens": true,
    "cmdf_exclusion_module": true
  }
}
