# Glossary

Plain-language definitions of terms used in this project. Added to as new terms come up.

**Design system:** the shared set of rules, values and building blocks a product is made from, so that every screen looks and behaves consistently and changes can be made in one place.

**Design token:** a named design value, such as `color-brand` or `space-4`. Components use the name, never the raw value, so changing the value updates everything that uses it.

**Primitive token:** a raw value with a neutral name, such as `blue-500 = #3647F5`. Describes what the value is.

**Semantic token:** a role that points at a primitive, such as `color-action = blue-500`. Describes what the value is for. Rebranding means re-pointing semantic tokens, not editing components.

**Figma variable:** Figma's version of a design token. A named value that layers and components can reference.

**Visual direction:** a candidate look for the product, mainly its colours and typefaces, shown on real screens so options can be compared before committing.

**Primary colour:** the brand colour used for the main action on a screen, such as the "Add chore" button.

**Accent colour:** a second colour used sparingly for small moments, such as the streak badge or the celebration, so the primary colour keeps its meaning.

**Typeface:** a family of letter shapes, such as Nunito. A display typeface is used for headings; a body typeface is used for reading text.

**Contrast ratio:** a measure of how readable one colour is on another, from 1:1 (invisible) to 21:1 (black on white). Normal text should reach at least 4.5:1.

**Component:** a reusable building block, such as a button or a chore row.

**Variant:** a version of a component for a different purpose, such as a primary button and an outline button.

**State:** how a component looks in a given moment: default, hover, pressed, focused, disabled, loading, error.

**Source of truth:** the one place a value or decision officially lives. Everything else copies from it.

**Happy path:** the route through the product when everything goes right, with no errors or detours.

**Usability test:** watching real people try to complete tasks with the product to see where they struggle.

**Accessibility:** making the product usable by people with different abilities, including low vision, keyboard-only use and screen readers.

**Repository (repo):** the project folder tracked by Git, with its full history. Ours is stored on GitHub.

**Commit:** a saved snapshot of the project with a message describing what changed.

**Markdown (.md):** a plain text format for documents, used here for the brief, the roadmap and the decision log because both people and Claude can read it cheaply.
