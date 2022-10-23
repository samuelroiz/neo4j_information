<html>
  <h1>APOC</h1>
  <p>Must insert "apoc.import.file.enabled=true" in <b> Settings </b>. </p>
  <p>Code:
  <ul><li>CALL apoc.help("")</li></ul>
  </p>
  <h3>Steps to use and unload APOC by using a <b> LOCAL FILE </b> </h3>
  <ol><li>Place JSON file in the import folder...<br><i>Example "C:\Users\sroiz\OneDrive\Desktop\Neo4j\relate-data\dbmss\dbms-91ae3d10-8063-4037-8000-7125ec599320\import"</i></li>
  <li>Run this code in Neo4j query: call apoc.load.json("file:/FedRAMP_rev4_MODERATE-baseline_profile.json")</li>
  </ol>
  <h3></h3>
  <ol>
  <li>Run this code in Neo4j query: call apoc.load.json("https://api.stackexchange.com/2.2/questions?pagesize=100&order=desc&sort=creation&tagged=neo4j&site=stackoverflow&filter=!5-i6Zw8Y)4W7vpy91PMYsKM-k9yzEsSC1_Uxlf")</li>
  </ol>
</html>
