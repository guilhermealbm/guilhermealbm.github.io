+++
date = '2026-01-25'
draft = false
title = 'Why Focus in Compose Is About Structure, Not Modifiers'
categories = ['Android']
languages = ['English']
+++
#### and/or: the most underrated interaction mechanism on Android is becoming important

About one and a half years ago, when I started to work focused (no pun intended!) on Android TV, I tried to anticipate what would change in my daily work. Other than a very different form factor and input type, I didn't expect many surprises. And, in a way, I was right. 

What I didn't anticipate was how tricky (and important) focus management would be.

At first, it felt like a TV-specific problem. But over time, it became clear that focus is no longer a TV thing. It shows up everywhere: ChromeOS, tablets, phones with keyboards or gamepads, and increasingly through accessibility requirements. Whether we like it or not, focus management is becoming a first-class citizen in Android’s ecosystem. 

Jetpack Compose is where this shift becomes really strong, because focus is no longer something implemented on top of the UI, but a direct consequence of how the UI is described and composed.

When I first started running into focus issues, my instinct was almost always the same: add more modifiers. Make something focusable, request focus manually, intercept key events. Sometimes this worked, but it rarely felt right. Small changes were often enough to break the behavior again.

Over time, I've realized most of these problems weren’t caused by missing modifiers, but by a deeper issue: not properly reasoning about focus traversal in a declarative UI. In Compose, focus doesn’t move between individual components in isolation, but through a hierarchy defined by the composition itself.

A simple example makes this easier to see. Imagine a layout with a vertical menu on the left and a list of content items on the right:

```kotlin
@Composable
fun FocusIssue() {
    Row {
        Column {
            repeat(3) {
                FocusableText(
                    text = "Menu $it",
                )
            }
        }
        Column {
            repeat(6) {
                FocusableText(
                    text = "Content $it",
                )
            }
        }
    }
}
```

| Menu column | Content column |
|-------------|----------------|
| Menu 0      | Content 0      |
| Menu 1      | Content 1      |
| Menu 2      | Content 2      |
|             | Content 3      |
|             | Content 4      |
|             | Content 5      |


At first, this looks straightforward. But if you navigate using a D-pad and keep pressing Down, something possibly surprising happens: once focus reaches Menu 2, pressing Down again moves focus to Content 3. From a user perspective, this feels wrong. They’re still interacting with the menu, yet focus suddenly jumps sideways into the content.

It’s tempting to "fix" this by addressing the symptom: override the traversal on the last menu item using focusProperties, canceling the Down direction, or manually redirecting focus. This approach could work, but it’s fragile. A small layout change is often enough to break the logic again.

The real issue here isn’t the last item. It’s the lack of structure in the focus hierarchy. From Compose’s point of view, all focusable children inside the Row belong to the same traversal scope. Once vertical movement is no longer possible in the left column, focus is free to move to whatever is geometrically next, which in this case is the right column.

If we instead express our intent declaratively and group related elements together, the problem disappears:

```kotlin
@Composable
fun FixedFocusIssue() {
    Row {
        Column(modifier = Modifier.focusGroup()) {
            repeat(3) {
                FocusableText(
                    text = "Menu $it",
                )
            }
        }
        Column(modifier = Modifier.focusGroup()) {
            repeat(6) {
                FocusableText(
                    text = "Content $it",
                )
            }
        }
    }
}
```

By adding focusGroup() to each column, we’re no longer adjusting individual nodes. Instead, we’re describing how focus is allowed to flow through the UI. Vertical navigation now stays within each group, and horizontal navigation moves between them, which matches both user expectations and the visual structure of the layout.

This shift in perspective was crucial for me. Taking a step back and thinking about how focus is allowed to flow through the UI was far more effective than trying to fix individual elements one by one.

The mental model behind focus traversal in Compose isn’t always straightforward, especially once conditional UI and recomposition come into play. Still, keeping this model in mind makes it much easier to satisfy focus requirements while keeping focus management simple, predictable, and resilient to change.

Once focus is understood as a consequence of how the UI is written, many problems stop being surprising. They become explainable, and, with time, avoidable. That understanding is the foundation for building Compose UIs that behave predictably across different input methods, not just on Android TV.
