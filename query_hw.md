*Find all time entries* <br>

SELECT * <br>
FROM time_entries; <br>

*Find the developer who joined most recently* <br>

SELECT MAX(created_at),* <br>
FROM time_entries; <br>

*Find the number of projects for each client* <br>

SELECT client_id, COUNT(*) AS project_count <br>
FROM projects <br>
GROUP BY client_id; <br>

*Find all time entries, and show each one's client name next to it* <br>

SELECT * <br>
FROM time_entries JOIN projects <br>
ON time_entries.project_id = projects.id; <br>

*Find all developers in the "Ohio sheep" group* <br>

SELECT developers.name, group_id <br>
FROM developers <br>
JOIN group_assignments <br>
ON group_assignments.developer_id = developers.id <br>
WHERE group_id = 3; <br>

*Find the total number of hours worked for each client* <br>

SELECT project_id, SUM(duration) AS total_hours <br>
FROM time_entries <br>
GROUP BY project_id; <br>

*Find the client for whom Mrs. Lupe Schowalter (the developer) has worked the greatest number of hours* <br>

SELECT developer_id, project_id, SUM(duration) AS hours_worked, name <br>
FROM time_entries <br>
JOIN projects ON projects.id = time_entries.project_id <br>
WHERE developer_id = 28 <br>
GROUP BY project_id  <br>
ORDER BY duration DESC  <br>
LIMIT 1; <br>

*List all client names with their project names (multiple rows for one client is fine).  Make sure that clients still show up even if they have no projects* <br>

SELECT projects.name AS project_name, clients.name AS client_name <br>
FROM projects <br>
JOIN clients ON clients.id = projects.client_id; <br>

*Find all developers who have written no comments* <br>

SELECT developers.name, comments.comment <br>
FROM developers <br>
LEFT JOIN comments <br>
ON comments.developer_id = developers.id <br>
Where comment IS null <br>



