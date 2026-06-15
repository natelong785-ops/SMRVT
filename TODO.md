## TODO
## Done TODOs are marked with #

#1. Incorporate a method of when Adding personnel having a drop down to assign them to a section.

#2. Incorporate a method of when "Editing" personnel having a drop down to assign them to a section.

#3. Fix the tile edit function.

#4. Remove "What-If" function from js and html.

#5. Find a method for having qualifications tied to each position. "The system must automatically enforce qualification-based logic to prevent uncertified personnel from being assigned to restricted slots" - 5.2.2 Stimulus A / 5.2.3 Req-4.
     **IMPLEMENTED: validateAssignment() in main.js, enforced in dragDrop.js and savePerson(). Admins configure reqQual per position via the Position Config modal. Default positions ship as open slots (no reqQual set); admins define requirements per deployment context.**

#6. Set up personnel to preload. Have these values preloaded into the project so when you run a new from scratch they're preloaded.
     **IMPLEMENTED: SAMPLE_PEOPLE array in config.js auto-loads on first run via loadState() fallback in state.js.**

#7. Future - Expand the import.csv file to include an almost complete squadron.

#8. Future - Split the script.js file into multiple files to cut down on long code. Helps on adding/removing features on the fly.
     **IMPLEMENTED: Codebase split into main.js, state.js, config.js, dragDrop.js, importExport.js, and metrics.js.**

9. Future - Figure out a method of "securing" the PII when exporting to a CSV and maybe have an unsecured export so that you can ensure there's a base that can be uploaded.

#10. Make sure to add % to each section. Filled against authorized.
     **IMPLEMENTED: Each section card shows live "% Section Readiness" calculated against authorized strength.**

#11. Fix font colors for status, total, assigned, readiness, medical/leave, deployment/tdy, filled/available/slots, role names, updated, drag to a slot, +add section.

#12. Incorporate a DB into the project.
     **IMPLEMENTED: PouchDB/IndexedDB for local persistence (state.js). Optional bidirectional CouchDB/Cloudant remote sync via startSync().**

#13. Add scrolling inside each section after XX amount.
     **IMPLEMENTED: .slots-scroll applies max-height: 520px with overflow-y: auto (style.css).**

14. Future - Figure out a method to have each "user" viewing rights for just their "section"; nesting of pages?

#15. Separate area that has all the deployed personnel. Move personnel to another section that cannot be deleted.
     **IMPLEMENTED: Dedicated "Deployed Personnel" drop zone in main. Drag here sets status to deployed and pins to the deployed panel.**

#16. Add an undo function for the session with 20 steps. Have a logging function for what has been done.
     **IMPLEMENTED: 20-step undo stack in state.js via takeSnapshot()/undo(). Ctrl+Z bound globally. Every mutation takes a snapshot before executing.**

#17. Work the What-If function back in.
     **IMPLEMENTED: toggleWhatIfMode(), commitWhatIf(), cancelWhatIf() in main.js. Amber banner with Commit / Discard controls. Database saving is paused during an active scenario.**

#18. Add date to personnel that they've been put into a section. Work "arrived" into this.
     **IMPLEMENTED: assignedDate stamped as ISO string on drag-drop (dragDrop.js) and modal save (main.js savePerson()). Displayed on the person card in the dates row.**

#19. "reset" function does not reset to default.
     **FIXED: clearState() in state.js calls defaultPeople() and defaultSections() for all branches and saves immediately.**

#20. Assignment does not work when adding a new person.
     **FIXED: savePerson() in main.js reads the f-assign-slot dropdown and applies section/slot to the new person object on creation.**

#21. When removing slots, personnel in those slots are not being shuffled to unassigned.
     **FIXED: changeSlots() and setRequired() in main.js find any occupant of the removed slot and set their section/slot to '' before popping the position.**

#22. Reset function does not reset the tiles back to default.
     **FIXED: clearState() restores BRANCHES[branchId].sections to a deep clone of the original config via defaultSections().**

#23. User cannot change name of sections.
     **FIXED: Admin-only renameSection() in main.js. Click the section title to rename inline.**

#24. User cannot delete/create sections.
     **FIXED: Admin-only addSection() and deleteSection() in main.js. Delete button visible on each section card for admins. + Add Section button shown for admins only.**

#25. Add function to admin that allows renaming sections already in the tracker.
     **FIXED: Same as #23 — renameSection() handles this. Also renameSlot() allows admins to double-click individual slot labels to rename them.**

#26. Remove user privilege to import.
     **FIXED: importCSV() checks currentUserRole — non-admins receive a toast error and the import is blocked. Import CSV and Template buttons are hidden from the UI for non-admin users at login.**
