[Code Golf Challenge](https://neo4j-code-golf-2022.devpost.com)

## Notes

<html>
  <ol>
    <li>To print out all node labels...</li>
    <ul>
      <li>MATCH (n) RETURN distinct labels(n)</li>
      <li>call db.labels();</li>
    </ul>
    <li>To print the node information...</li>
      <ul>
        <li>MATCH (m:Movie) RETURN m</li>
      </ul>
  </ol>
</html>

<html>
  <h3>How to import files</h3>
  <details>
    <summary>CSV Files</summary>
    <p>Code example: <br> LOAD CSV WITH HEADERS FROM 'file:///test.csv' AS line 
       <br> MERGE (n:MyNode {Name:line.Client})
       <br> MERGE (m:MyNode {Name:line.Year_joined})
       <br> MERGE (n) -[:TO {dist:line.Description}]-> (m)
    </p>
  </details>
</html>
