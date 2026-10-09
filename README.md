# QuizLive — deploy

Files:
- index.html — player page (phones). The QR code points here.
- host.html  — host/projector page.

## Publish on GitHub Pages
1. In your repository: Add file → Upload files → drag in index.html and host.html (and this README) → Commit changes.
2. Settings → Pages → Build and deployment → Deploy from a branch → main / (root) → Save.
3. Wait 1–2 minutes. Your game is live at:
   - Host:    https://<your-username>.github.io/<repo-name>/host.html
   - Players: https://<your-username>.github.io/<repo-name>/  (or scan the QR code)

## Running a game
- Open host.html on the laptop connected to the projector. Wait for the green "Live" dot, top right.
- Players scan the QR code or open the player link and enter the PIN.
- Click Start game. Use the bottom-right button to move through each question.
- Refreshing the host page keeps the current game. "New game" on the final screen creates a new PIN.

## Adding your own questions
On host.html, in the lobby, click "Questions". Upload a CSV with columns:
question, answer_a, answer_b, answer_c, answer_d, correct (A–D), time_seconds (optional), explanation (optional).
Click "Download template" for an example. Two to four answers per question; up to 100 questions. Saved in that browser.

## Testing without phones
Open host.html?bots=30 to add 30 simulated players (they only exist on the host screen).

## Notes
- Real-time sync runs through your Supabase project (Realtime Broadcast). No database tables are needed.
- The host browser is the game's authority: it runs the timer, accepts or rejects answers by its own clock and calculates scores. Keep the host tab open for the whole game.
- Up to 400 players per game. Supabase's free plan allows about 200 simultaneous connections, so games above ~190 players need the Supabase Pro plan (500 connections). Test with your real group size before an important event.
