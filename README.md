[Code Golf Challenge](https://neo4j-code-golf-2022.devpost.com)

## Notes

<html>
  <ol>
    <li>To print out all node labels...</li>
    <ul>
      <li>MATCH (n) RETURN distinct labels(n)</li>
      <li>call db.labels();</li>
    </ul>
    <li>
      <ol>To print the node information...</ol>
      <ul>
        <li>MATCH (m:Movie) RETURN m</li>
      </ul>
    </li>
  </ol>
</html>
