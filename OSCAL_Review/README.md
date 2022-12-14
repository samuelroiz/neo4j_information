<html>
  <h1>APOC</h1>
  <p>Must insert "apoc.import.file.enabled=true" in <b> Settings </b>. </p>
  <p>Code:
  <ul><li>CALL apoc.help("")</li></ul>
  </p>
  <h3>Steps to use and unload APOC by using a <b> LOCAL FILE </b> </h3>
  <ol><li>Place JSON file in the import folder...<br><i>Example "C:\Users\sroiz\OneDrive\Desktop\Neo4j\relate-data\dbmss\dbms-91ae3d10-8063-4037-8000-7125ec599320\import"</i></li>
  <li>Run this code in Neo4j query: <br> call apoc.load.json("file:/FedRAMP_rev4_MODERATE-baseline_profile.json")</li>
  </ol>
  <h3>Steps to use and unload APOC by using a <b> LINK/URL </b></h3>
  <p><b>Note(s): </b><br> The URL is <a href="https://api.stackexchange.com/2.2/questions?pagesize=100&order=desc&sort=creation&tagged=neo4j&site=stackoverflow&filter=!5-i6Zw8Y)4W7vpy91PMYsKM-k9yzEsSC1_Uxlf"> Stackoverflow 100 pages </a> and it has 100 pages. The examples we are going to use is reducing the 100 pages to 5 pages to avoid buffering. <i>To change the pages is by converting "pagesize=" to a number you want. </i> </p>
  <ol>
  <li>Run this code in Neo4j query: <br> call apoc.load.json("https://api.stackexchange.com/2.2/questions?pagesize=5&order=desc&sort=creation&tagged=neo4j&site=stackoverflow&filter=!5-i6Zw8Y)4W7vpy91PMYsKM-k9yzEsSC1_Uxlf")</li>
  
  <li>Check the key(s) in the JSON by using this code: <br> call apoc.load.json("https://api.stackexchange.com/2.2/questions?pagesize=5&order=desc&sort=creation&tagged=neo4j&site=stackoverflow&filter=!5-i6Zw8Y)4W7vpy91PMYsKM-k9yzEsSC1_Uxlf") yield value
unwind value.items as q
return keys(q)</li>
  <li>To return a table with selected key(s) from URL by using this code: <br> call apoc.load.json("https://api.stackexchange.com/2.2/questions?pagesize=5&order=desc&sort=creation&tagged=neo4j&site=stackoverflow&filter=!5-i6Zw8Y)4W7vpy91PMYsKM-k9yzEsSC1_Uxlf") yield value <br>
unwind value.items as q <br>
return keys(q)</li>
  </ol>
  <li>call apoc.load.json("https://api.stackexchange.com/2.2/questions?pagesize=5&order=desc&sort=creation&tagged=neo4j&site=stackoverflow&filter=!5-i6Zw8Y)4W7vpy91PMYsKM-k9yzEsSC1_Uxlf") yield value <br>
unwind value.items as q <br>
merge(question:Question {id:q.question_id}) ON CREATE SET question.title = q.title, question.answered = q.is_answered <br>
merge(u:User {name:q.owner.display_name}) <br>
merge (u)-[:ANSWERED]->(question) <br>
foreach (t in q.tags | MERGE (tag:Tag {name:t}) MERGE (question)-[:TAGGED]->(t))</li> <br>
  <h4>Random examples by using URL</h4>
  <li>How to only choose the first 1 - 10 pages: <br> UNWIND range(1,10) as page
WITH "https://api.stackexchange.com/2.2/questions?page="+page+"&pagesize=100&order=desc&sort=creation&tagged=neo4j&site=stackoverflow&filter=!5-i6Zw8Y)4W7vpy91PMYsKM-k9yzEsSC1_Uxlf" AS url
CALL apoc.load.json(url) YIELD value <br>
UNWIND value.items AS q <br>
MERGE (question:Question {id:q.question_id}) <br>
ON CREATE SET question.title = q.title, question.share_link = q.share_link, question.favorite_count = q.favorite_count, question.creation_date = q.creation_date <br></li>
<li>
  call apoc.load.json("https://raw.githubusercontent.com/GSA/fedramp-automation/master/dist/content/baselines/rev4/json/FedRAMP_rev4_MODERATE-baseline_profile.json") <br> yield value <br>
unwind value.profile as q return keys(q) <br>
</li>

</html>

call apoc.load.json("https://api.stackexchange.com/2.2/questions?pagesize=5&order=desc&sort=creation&tagged=neo4j&site=stackoverflow&filter=!5-i6Zw8Y)4W7vpy91PMYsKM-k9yzEsSC1_Uxlf") yield value
unwind value.items as q
merge (question:Question {id:q.question_id}) ON CREATE SET question.title = q.title, question.answered = q.is_answered
merge (u:User {name:q.owner.display_name})
merge (u)-[:ANSWERED]->(question)
foreach(t in q.tags | MERGE (tag:Tag {name:t}) MERGE (question)-[:TAGGED]->(t))

