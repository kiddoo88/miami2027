# Verification

Browser verification completed in the Codex in-app browser on 28–29 October 2026.

## Passed

- JavaScript syntax checks for app.js and data.js.
- All six views render: Overview, Itinerary, Photo spots, Stays, Bookings, Budget.
- Responsive geometry checks at 320, 768, and 1366 CSS pixels: no document-level horizontal overflow; no failed image loads observed. Additional visual inspection at 390 pixels and desktop size.
- Add an activity with a custom time and details, move it up, mark complete, save a daily note, reload: all changes survive.
- A literal `<script>` string in an activity detail renders as text.
- Update a booking to confirmed with a test reference, reload: confirmed count and reference survive.
- Add a photo favorite and filter to saved places: correct card remains visible.
- Set a USD 5,000 budget and 35 THB/USD rate; add THB 3,500 food expense: total USD 100, remaining USD 4,900, 2% budget usage, food category USD 100. Values survive reload.
- Export JSON through the app: a file is downloaded.
- Import the exported file through the file picker: confirmation appears, successful import message shown, budget values preserved.
- Reset through its confirmation flow: restored all bookings to pending and removed test activities/notes/expenses.
- No browser console errors observed during functional tests.

## To check again

1. Start the server described in README.md.
2. Open the itinerary and select each date. Confirm arrival 16 Jan 16:55 and departure 24 Jan 18:45.
3. Add and edit an activity, move it, mark complete, save a note, reload.
4. Update one booking. Check the matching accommodation status and Overview count.
5. Add USD and THB expenses, edit the rate, and confirm recalculation.
6. Export a backup, make another edit, then import the backup and confirm replacement.
7. Test a malformed backup: the app should reject it without replacing existing state.

## Scope of verification

This verifies the app's behavior and layout, not operator availability, 2027 prices, reservation validity, weather, live traffic, or the conference program. No real reservations were made. Cross-device synchronization is intentionally manual through JSON backup. Mobile Safari and Android Chrome were not tested on physical devices.
