# 8Pool — Pool Table Timer & Billing Control (C# WinForms)

A Windows Forms desktop application built in C# (.NET Framework) featuring a reusable custom `PoolTable` `UserControl` for tracking table playtime, formatting elapsed time (`hh:mm:ss`), calculating hourly session fees, and notifying the parent form via custom events.

## Features

- **Reusable Custom `UserControl` (`PoolTable`)**: Can be placed multiple times on a form (e.g., multiple pool tables in a hall) and configured directly from the Visual Studio Properties window under the **Pool Config** category:
  - `TableTitle` — Sets the group box title (default: `"Table"`).
  - `TablePlayer` — Sets the active player label (default: `"Player"`).
  - `HourlyRate` — Sets the hourly billing rate (default: `10.00f`).
- **Session Timer Controls**:
  - **Start / Stop** button toggles the timer (`timer1`) and updates elapsed time every second in `hh:mm:ss` format (`00:00:00`).
  - Quick player name editing via `toolStripTextBox1`.
- **Billing & Event Notification (`OnTableComplete`)**:
  - Clicking **End** stops the timer, calculates total fees based on elapsed seconds and `HourlyRate`, raises `OnTableComplete` with `TableCompletedEventArgs` (`TimeText`, `TimeInSeconds`, `RatePerHour`, `TotalFees`), and resets the table state.
- **Host Form Integration (`Form1`)**: Subscribes to `OnTableComplete` (`poolTable_OnTableComplete`) and displays a summary `MessageBox` with time consumed, total seconds, hourly rate, and total fees.

## Tech Stack

- **Language**: C#
- **UI Framework**: Windows Forms (.NET Framework)
- **IDE**: Visual Studio

## Project Structure

- `PoolTable.cs` — Custom `UserControl`, `TableCompletedEventArgs`, `OnTableComplete` event, timer logic, and fee calculation.
- `Form1.cs` — Main form hosting `PoolTable` control(s) and handling session completion events.

## Getting Started

1. Clone or download the repository from GitHub.
2. Open the solution (`.sln`) in **Visual Studio** on Windows.
3. Build the solution (`Ctrl + Shift + B`) so the `PoolTable` user control is compiled and available in the Toolbox / Designer.
4. Run the project (`F5`) to test starting, pausing/stopping, and ending a table session.
