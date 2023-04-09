# Testing Multiplayer Projects

When creating games with UEFN/Verse that are multiplayer games, it's important to test those creations with multiple players. You'll want to discover any issues before publishing your island.

The steps required to test an unpublished island is currently a little awkward but not impossible:

1. Start up UEFN.
2. Open your project.
3. Click **Launch Session** in UEFN.
4. Wait for Fortnite to start and put you in a UEFN session.
5. Open the Fortnite sidebar menu and choose **Return to Lobby**.
6. Back in the "Play" tab the Game mode should be listed as "UEFN Session".
7. Press **Play**, and you'll be sent to what looks like a "simulation" room - digital walls, windows and a few trees.
8. Open the Fortnite sidebar menu and invite other people to your party.
9. After joining the party other players will see "Creative" as their current Game mode.
10. Other players should press **Play** to join you in the "simulation" room.
11. Once everybody has joined and is in the "simulation" room you're ready to proceed.
12. Back in UEFN click **Launch Session** again.
13. All players should see "Edit Mode PREPARING..."
14. After a few moments you'll be back in your island in Edit mode.
15. Open the Fortnite sidebar menu and choose **Start Game**.

Important Note: All players are currently able to edit things while in Edit mode.

## Using Multiple UEFN Clients

When you want to create with a team of creators where multiple people are using UEFN for the same project, you will need to create a team. To create a team, go to the [Fortnite Creator Portal]({{ book.external.links.fortnite_create }}) and sign in. Once you've signed in, you can create a new team and add teammates to that team. You can also add more creators to existing teams as well.

> *ALL* creators must be *18+ years old* to be in a team and create experiences using UEFN.

> Visit Epic's [Creating Teams in Creator Portal]({{ book.external.links.fortnite_creative_team_docs }}) documentation to learn more about team projects.

Once you have created your team and invited your teammates, you will have to create a new experience under that team. It doesn't look to be possible to migrate existing projects to a team.

> Be sure to use the [Unreal Revision Control System]({{ book.external.links.uefn_unreal.revision_control }}) to be able to share the project's state with teammates!

Once you have the project open in UEFN, have a *single* teammate (doesn't matter who) start the session as normal via the `Launch Session` button in the toolbar. Once they are connected to the session *and* in the playtest map with their character, then the other teammates can also click the `Launch Session` button and that will bring their character into the playtest map as well as allow them to modify the map with their UEFN client and show up in the playtest map.

Epic Games' [Collaborating in Unreal Editor for Fortnite]({{ book.external.links.uefn_collaboration }}) documentation describes well the process for collaborating with a team so be sure to check that out as well!
