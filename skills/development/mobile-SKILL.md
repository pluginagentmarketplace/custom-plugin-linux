---
name: mobile
description: Mobile development skill - iOS, Android, React Native, Flutter
version: "1.0.0"
sasmp_version: "1.3.0"

input_schema:
  type: object
  properties:
    task: { type: string, enum: [build, debug, optimize, deploy, test] }
    platform: { type: string, enum: [ios, android, react_native, flutter] }
  required: [task, platform]

output_schema:
  type: object
  properties:
    code: { type: string }
    config: { type: string }
    best_practices: { type: array }

retry_config:
  max_attempts: 3
  backoff: exponential

timeout_ms: 30000
---

# Mobile Development Skill

## PURPOSE
Native and cross-platform mobile app development.

## CORE COMPETENCIES
```
iOS:
├── Swift/SwiftUI
├── UIKit
├── Core Data
└── Combine

Android:
├── Kotlin
├── Jetpack Compose
├── Room
└── Coroutines

Cross-Platform:
├── React Native
├── Flutter/Dart
├── State management
└── Native modules
```

## CODE PATTERNS

### SwiftUI View
```swift
struct ContentView: View {
    @StateObject private var viewModel = ContentViewModel()

    var body: some View {
        NavigationStack {
            List(viewModel.items) { item in
                ItemRow(item: item)
            }
            .refreshable { await viewModel.refresh() }
            .task { await viewModel.load() }
        }
    }
}
```

### Kotlin Compose
```kotlin
@Composable
fun ItemScreen(viewModel: ItemViewModel = hiltViewModel()) {
    val items by viewModel.items.collectAsStateWithLifecycle()

    LazyColumn {
        items(items) { item ->
            ItemCard(item = item)
        }
    }
}
```

## TROUBLESHOOTING

| Issue | Cause | Solution |
|-------|-------|----------|
| App rejected | Guideline violation | Review rejection reason |
| Slow launch | Heavy initialization | Lazy load, defer work |
| Memory leak | Retained references | Use weak references |
| Crash on background | State not saved | Persist state properly |
