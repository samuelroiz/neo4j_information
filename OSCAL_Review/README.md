<html>
  <h3>APOC</h3>
  <p>Must insert "apoc.import.file.enabled=true" in <b> Settings </b>. </p>
  <p>Code:
  <ul><li>CALL apoc.help("")</li></ul>
  </p>
  <p>Steps to use and unload APOC
  </p>
  <ol><li>Place JSON file in the import folder...<br><i>Example "C:\Users\sroiz\OneDrive\Desktop\Neo4j\relate-data\dbmss\dbms-91ae3d10-8063-4037-8000-7125ec599320\import"</i></li>
  <li>Run this code in Neo4j query: call apoc.load.json("file:/FedRAMP_rev4_MODERATE-baseline_profile.json")</li>
  </ol>
</html>
