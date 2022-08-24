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
    <li>To delete all data and nodes...</li>
    <ul>
      <li>match (a) -[r] -> () delete a, r</li>
      <li>match (a) delete a</li>
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
       <br>
       <br> LOAD CSV WITH HEADERS FROM 'file:///test.csv' AS line
       <br> MERGE (n:MyNode {Name:line.Client})
       <br> MERGE (m:MyNode {Name:line.Year_joined})
       <br> MERGE (d:MyNode {Name:line.Description})
       <br> MERGE (n) -[:TO {dist:line.Description}]-> (m)
       <br> MERGE (d) -[:TO {dist:line.Year_joined}]-> (n)
       <br>
       <br>
       <br> LOAD CSV WITH HEADERS FROM 'file:///disney_plus_titles.csv' AS disney with disney where disney.director is not null AND disney.cast is not null AND disney.country is not null
      <br> MERGE (s:disney {ID:disney.show_id})
      <br> MERGE (t:disney {Type:disney.type})
      <br> MERGE (l:disney {Title:disney.title})
      <br> MERGE (d:disney {Director:disney.director})
      <br> MERGE (c:disney {Cast:disney.cast})
      <br> MERGE (u:disney {Country:disney.country})
      <br> MERGE (e:disney {Year:disney.release_year})
      <br> MERGE (r:disney {Rating:disney.rating})
      <br> MERGE (a:disney {Length:disney.duration})
      <br> MERGE (i:disney {Genre:disney.listed_in})
      <br> MERGE (p:disney {Summary:disney.description})
      <br> MERGE (d) -[:TO {date:disney.release_year}]-> (l)
      <br> MERGE (c) -[:TO {date:disney.release_year}]-> (l)
      <br> MERGE (l) -[:TO ]-> (s)
      <br> MERGE (p) -[:TO ]-> (l)
      <br> MERGE (l) -[:TO {rating:disney.rating}]-> (t)
      <br> MERGE (u) -[:TO {rating:disney.rating}]-> (t)
      <br> MERGE (t) -[:TO ]-> (i)
      <br>
      <br>
      <br> LOAD CSV WITH HEADERS FROM 'file:///disney_plus_titles.csv' AS disney with disney where disney.director is not null AND disney.cast is not null AND disney.country is not null
      <br> MERGE (s:ID {ID:disney.show_id})
      <br> MERGE (t:INFO {Type:disney.type})
      <br> MERGE (l:INFO {Title:disney.title})
      <br> MERGE (d:CREDITS {Director:disney.director})
      <br> MERGE (c:CREDITS {Cast:disney.cast})
      <br> MERGE (u:LOCATION {Country:disney.country})
      <br> MERGE (e:INFO {Year:disney.release_year})
      <br> MERGE (r:INFO {Rating:disney.rating})
      <br> MERGE (a:INFO {Length:disney.duration})
      <br> MERGE (i:INFO {Genre:disney.listed_in})
      <br> MERGE (p:INFO {Summary:disney.description})
      <br> MERGE (d) -[:YEAR {date:disney.release_year}]-> (l)
      <br> MERGE (c) -[:YEAR {date:disney.release_year}]-> (l)
      <br> MERGE (s) -[:YEAR {date:disney.release_year}]-> (p)
      <br> MERGE (l) -[:TO ]-> (s)
      <br> MERGE (p) -[:TO ]-> (l)
      <br> MERGE (l) -[:RATING {rating:disney.rating}]-> (t)
      <br> MERGE (u) -[:RATING {rating:disney.rating}]-> (t)
      <br> MERGE (t) -[:TO ]-> (i)
      <br>
      <br>
      <br> LOAD CSV WITH HEADERS FROM 'file:///disney_plus_titles.csv' AS disney with disney where disney.director is not null AND disney.cast is not null AND disney.country is not null
      <br> MERGE (s:ID {ID:disney.show_id})
      <br> MERGE (t:INFO {Type:disney.type})
      <br> MERGE (l:INFO {Title:disney.title})
      <br> MERGE (d:CREDITS {Director:disney.director})
      <br> MERGE (c:CREDITS {Cast:disney.cast})
      <br> MERGE (u:LOCATION {Country:disney.country})
      <br> MERGE (e:INFO {Year:disney.release_year})
      <br> MERGE (r:INFO {Rating:disney.rating})
      <br> MERGE (a:INFO {Length:disney.duration})
      <br> MERGE (i:INFO {Genre:disney.listed_in})
      <br> MERGE (p:INFO {Summary:disney.description})
      <br> MERGE (d) -[:YEAR {date:disney.release_year}]-> (l) <- [:YEAR {date:disney.release_year} ]- (c)
      <br> MERGE (l) -[:ID {ID:disney.show_id}]-> (s)
      <br> MERGE (l) -[:INFO ]- (t) -[:INFO ]- (e) -[:INFO ]- (r) -[:INFO ]- (a) -[:INFO]- (i) -[:INFO]- (p) -[:LOCATION]- (u)
      <br>
      <br>
      <br>
      <br> LOAD CSV WITH HEADERS FROM 'file:///disney_plus_titles.csv' AS disney with disney where disney.director is not null AND disney.cast is not null AND disney.country is not null
      <br> MERGE (s:ID {ID:disney.show_id})
      <br> MERGE (t:TYPE {Type:disney.type})
      <br> MERGE (l:TITLE {Title:disney.title})
      <br> MERGE (d:CREDITS {Director:disney.director})
      <br> MERGE (c:CREDITS {Cast:disney.cast})
      <br> MERGE (u:LOCATION {Country:disney.country})
      <br> MERGE (e:RELEASE {Year:disney.release_year})
      <br> MERGE (r:RATING {Rating:disney.rating})
      <br> MERGE (a:DURATION {Length:disney.duration})
      <br> MERGE (i:GENRE {Genre:disney.listed_in})
      <br> MERGE (p:INFO {Summary:disney.description})
      <br> MERGE (d) -[:year {date:disney.release_year}]-> (l) <- [:year {date:disney.release_year} ]- (c)
      <br> MERGE (l) -[:id {ID:disney.show_id}]-> (s)
      <br> MERGE (t) -[:type {TYPE:disney.type}]-> (s)
      <br> MERGE (l) -[:title ]-> (i)
      <br> MERGE (u) -[:location ]-> (i) 
      <br> MERGE (r) -[:rating ]-> (p) 
      <br> MERGE (a) -[:length ]-> (p) 
      <br> MERGE (p) -[:summary]-> (l) 


    </p>
  </details>
  <details>
    <summary>Youtube Links</summary>
    <p><br> <a href="https://www.youtube.com/watch?v=npOMyKnmgMI">Import CSV file in NEO4j by Gephi</a>
      <br> <a href="https://www.youtube.com/watch?v=J8vmqJrqd6w&t=309s">How to import CSV into Neo4j? | Neo4j Tutorial for Beginners | Let's have a look @ LOAD CSV | Part 3</a>
    </p>
  </details>
</html>
