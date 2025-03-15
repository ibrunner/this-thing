# Disting mk4 MIDI Controller - Design Document

## 1. Project Overview

The Disting mk4 MIDI Controller is a React Native application built with Expo to facilitate easy program selection and parameter control of the Expert Sleepers Disting mk4 Eurorack module via MIDI. The app aims to solve the discovery problem inherent in the module's deep but sometimes hard-to-navigate interface.

### Key Features

- Browse, search, and select Disting programs through an intuitive interface
- Control program parameters via MIDI
- Favorites system for quick access to commonly used programs
- Algorithm categorization for easier discovery
- MIDI channel configuration

## 2. Technical Specifications

### Framework & Libraries

- React Native with Expo
- Potential libraries:
  - `react-native-midi` or similar for MIDI communication
  - React Navigation for app navigation
  - Async Storage for local data persistence
  - Reanimated for smooth animations (if needed)

### Device Compatibility

- iOS initially (leveraging iOS CoreMIDI support)
- Android expansion possible in future iterations

## 3. User Interface Design

### Color Scheme

- Dark theme with white text to match the Disting module's aesthetic
- Primary: Black (#000000)
- Secondary: Dark Gray (#222222)
- Accent: White (#FFFFFF)
- Optional accent colors for categories

### Design Philosophy

- Two potential design directions:
  1. **Minimalist**: Clean, modern interface with simple controls
  2. **Skeuomorphic**: Interface mimicking the hardware appearance with virtual LEDs and knobs

### Screen Navigation Flow

1. **Home Screen**: Program browser with category filters, search, and favorites
2. **Program Control Screen**: Parameter controls and description for selected program
3. **Settings Screen**: MIDI configuration and app preferences

## 4. Program Organization

Based on the Disting mk4's 128 algorithms (A-1 through P-8), we propose the following category structure to improve discoverability:

1. **Audio Effects**

   - Delays/Echoes
   - Reverbs
   - Filters
   - Modulation Effects (Chorus, Phaser, etc.)
   - Distortion
   - Dynamics (Compressors, Gates)

2. **Synthesis**

   - VCOs
   - LFOs
   - Envelope Generators
   - Wavetable Algorithms
   - Granular Synthesis

3. **Utilities**

   - Logic
   - Mixing/Routing
   - Sample & Hold
   - Quantizers
   - Pitch/CV Processing

4. **MIDI & Clock**

   - MIDI Converters
   - Clock Generation/Processing
   - MIDI File Players

5. **Sample Playback**
   - Audio Players
   - Loopers
   - Recorders
   - Multisample Players

Each algorithm will belong to one or more categories to facilitate easy discovery.

## 5. Feature Details

### Program Browser (MVP Priority)

- List view of all programs
- Grid view as an option
- Send MIDI program change messages on selection
- Program details view with description
- Category filtering
- Text search
- Recently used programs
- Favorites section

### Program Controls

- Generic UI initially with up to 8 parameter controls
- Visual representation of parameter values
- Z knob/CV control
- Parameter names and ranges displayed
- Save/load preset (future feature)

### Favorites System

- Add/remove programs from favorites
- Reorder favorites
- Optional custom naming for favorites

### MIDI Configuration

- MIDI channel selection (1-16)
- MIDI device connection status
- MIDI thru options

## 6. Development Roadmap

### Phase 1 (MVP)

- Basic setup and structure
- **Program Selection and Browsing**
  - List view of all algorithms
  - MIDI program change on selection
  - Program view with description
  - Simple categorization

### Phase 2

- Enhanced program browser
  - Additional views (grid, etc.)
  - Advanced search and filtering
  - Favorites system
- Basic parameter control interface
- MIDI channel configuration

### Phase 3

- Complete parameter control for all algorithms
- Enhanced visual feedback
- Refined categorization system

### Phase 4

- Algorithm-specific UIs for popular programs
- Presets storage and recall
- Advanced MIDI features

### Phase 5

- Android support
- Cloud sync for presets
- Community feature for sharing presets

## 7. Implementation Notes

### MIDI Communication

- Use CC messages 1-6 for parameters 0-5
- Use CC 17 for Z control
- Use CC 18 for algorithm selection
- Program change messages for algorithm/preset selection (configurable)

### Data Storage

- Local storage for favorites and recent programs
- Future preset storage structure

### Performance Considerations

- Minimize interface lag in MIDI communication
- Optimize rendering for parameter changes
- Handle MIDI connection stability
