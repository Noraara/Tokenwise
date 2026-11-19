# Graph retrieval

Use an existing project graph when the question is about relationships and a narrow query can avoid several exploratory reads.

1. Identify the relevant project, module or vault scope. Locate the graph through the project index or the configured tool. With Graphify, a common default is `graphify-out/graph.json`.
2. Check the graph's scope and freshness using the project's index metadata, indexed revision or changed source files as available. If you cannot establish that it covers the relevant sources and reflects material changes, switch to targeted search.
3. Run one focused query with the specific names and relationship you need. With Graphify, check `graphify query --help` or the installed tool's docs for graph selection, depth and output controls. A command may look like this, depending on the installed version:

   ```sh
   graphify query "Which modules call SubmitClaim?" --graph graphify-out/graph.json --depth 2 --budget 800
   ```

4. Use the returned paths to open the decisive definitions and references. Verify dynamic dispatch, runtime wiring and inferred edges directly. If a node is missing, the result is ambiguous or output is too broad, narrow once when the fix is clear. Otherwise trace the relationship in source.

Keep the returned evidence small enough to be useful. A tool's budget can be approximate. Avoid dumping the whole graph into context. Record durable conclusions only when the task calls for a knowledge update.

An index has a build and maintenance cost. Consider that work separately when similar queries recur and the user has authorized indexing the intended scope.
