# Phase 3: Local Voice Setup

## Objective

Configure local speech-to-text (STT) for Nacho without using cloud transcription or AI services.

## Verified Environment

- Operating system: Windows 64-bit
- Assistant: Hermes Agent v0.23.3
- Local model: Qwen3.5 9B Q4_K_M
- Inference provider: Hermes-managed llama.cpp with CUDA
- Local inference endpoint: http://127.0.0.1:18434/v1
- Python runtime: Hermes-managed Python 3.14.9

## STT Configuration

Hermes STT provider is configured as:

    stt.provider = local

The following packages successfully import from the active Hermes runtime:

| Package | Verified version |
|---|---:|
| faster-whisper | 1.2.1 |
| av | 18.1.0 |
| sounddevice | 0.5.6 |
| numpy | 2.5.4 |

Hermes local STT model configuration currently specifies:

    model: base
    language: ''
    vad: true

The active Python environment is managed by Hermes. Its location may change after a Hermes runtime update. Use `hermes doctor` to identify the active runtime rather than assuming an old virtual-environment path remains valid.

## Installation

The Hermes voice dependency group was installed with:

    hermes pm install --extra voice

The active runtime was then checked by importing the packages listed above.

## Current Status

Verified:
- Local STT provider selected in Hermes configuration.
- Required voice dependencies import successfully.
- Hermes doctor reports all checks passed.
- Local LLM inference has been tested independently.

Not yet verified:
- Microphone device detection and recording.
- Successful local Whisper transcription from live microphone audio.
- Desktop microphone integration.
- Local text-to-speech (TTS).
- Wake-word detection and continuous voice interaction.

Package installation alone does not establish that microphone transcription works.

## Privacy and Security Requirements

- Do not configure cloud STT or TTS providers.
- Do not add cloud AI API keys.
- Do not activate cloud voice or live-conversation services.
- Keep local inference and local voice processing as the default.
- Document and verify any future external integration before enabling it.

## Next Steps

1. Verify that Hermes detects the intended microphone.
2. Test local transcription using the configured Whisper model.
3. Verify that the desktop microphone control uses the local provider.
4. Evaluate a local TTS engine separately.
5. Test wake-word detection only after basic STT and TTS work.
