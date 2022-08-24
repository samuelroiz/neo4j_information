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
  <h4>CSV Files</h4>
  <details>
    <summary>Code Examples</summary>
    <p><br> LOAD CSV WITH HEADERS FROM 'file:///test.csv' AS line 
       <br> MERGE (n:MyNode {Name:line.Client})
       <br> MERGE (m:MyNode {Name:line.Year_joined})
       <br> MERGE (n) -[:TO {dist:line.Description}]-> (m)
    </p>
  </details>
  <details>
    <summary>Youtube Links</summary>
    <p><br> <a href="https://www.youtube.com/watch?v=npOMyKnmgMI">Import CSV file in NEO4j by Gephi</a>
      <br> <a href="https://www.youtube.com/watch?v=J8vmqJrqd6w&t=309s">How to import CSV into Neo4j? | Neo4j Tutorial for Beginners | Let's have a look @ LOAD CSV | Part 3</a>
    </p>
  </details>
</html>

