# Council inspection form: sandbox replica

Practice target for the bot that transfers Insight Companion inspections into the council system. Nothing leaves the browser.

## Run
```
node serve.js
```
Open http://localhost:8765. (Opening index.html as a file also works in a normal browser.)

## Flow it mimics
1. **Insert** on the grid creates a new inspection (WF = New) and opens the form.
2. Fill the 7 tabs: Park, Equipment, Component, Undersurface/Environment, Trees/Others, Softfall Required, Comments/Inspector. **Save** sets WF = Completed.
3. Later: select the row in the grid, hamburger menu > **Photos**. Click **Upload**, choose a file, type the **Caption**, click **Save**. Repeat per photo.

## Validation (mirrors the live form)
- InspectionType and Inspector are mandatory (both pre-filled).
- 1.01r Comments is mandatory when the 1.01r rating is greater than 3.
- Caption is required to save a photo (sandbox rule, so the bot can't skip it).

## Checking what the bot did
- Menu > **Sandbox: Export JSON** downloads every record and its photo captions.
- In the console: `__sandbox.records()`.
- Menu > **Sandbox: Reset data** wipes and reseeds (3 fake parks).

## Assumptions to check against the real system
- Dropdown option lists are placeholders. Ratings are 1 to 5; Estimated Age, Playground Ref, Softfall Unit and InspectionType lists are guesses. Replace them with the real lists from the live form.
- Photo caption: the live screen shows one text box with "123" beside Save / Cancel / Rotate / Upload. I treated it as the caption and put it before Upload. Confirm the real order (caption before or after choosing the file).
- Seed data is fake. No client names, parks or addresses were copied.
- Menu items other than Main, Form, Photos are stubs.
