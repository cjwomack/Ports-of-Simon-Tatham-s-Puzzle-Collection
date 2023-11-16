Here are some instructions I worked out to compile for Mac - Mac isn't my daily driver so excuse any mistakes. I did volunteer by email to compile this since Mr Tatham's Mac has died but I have not received a response. </br></br>
Perhaps because I didn't realised that Debian had already had a .deb for his puzzles it made me sound stupid as I have pulled out a old PPC Powerbook to practise cross-compiling, study has been in bioinformatics so less depth as Comp Sci student though continuing studies in Comp Sci

**Worked Under Mac OS X Catalina**

1. install cmake via macports (potentially you need to install more dependencies, previously I have install octave via macports so perhaps gtk or clang or gcc have been downloaded from this)
  sudo port install cmake

2. download halibut
git clone --recursive https://git.tartarus.org/simon/halibut.git
3. cd halibut
   cmake .
4. cmake --build .
5. cp halibut /usr/local/bin or some other path on path
6. download games
git clone https://git.tartarus.org/simon/puzzles.git
7. Find the last commit id
   cd puzzles/.git/info </br>
   git log --oneline -n 1
8. change the version number to "YYYYMMDD.#lastcommitid" instead "Unidentified build" of in version.h 
   cd ../../</br>
   vim version.h
9. cmake .
10. cmake --build .
11. cp Puzzles.app a_folder_somewhere
12. Use the applications shortcut in your previous .dmg and copy to a_folder_somewhere
13. cd a_folder_somewhere
14. hdiutil create -volname "Simon Tatham's Puzzle Collection"  -srcfolder .  -ov -format UDCO -fs HFS+ ../puzzles.dmg
