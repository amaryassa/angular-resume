### "start": "concurrently -k -n \"Angular,BDD\" -p \"[{name}]\" -c \"blue,green\" \"ng serve\" \"json-server --watch db.json\"",

ng g m posts
for %n in (posts/add-post ,posts/edit-post ,posts/list-posts ,posts/single-post) do ng g c %n --skipTests

for %n in (models/post, models/user) do ng g class %n --type=model --skipTests

for %n in (services/post, services/auth) do ng g s %n --skipTests

for %n in (src/posts/state, services/auth) do ng g s %n

---

ngrx:

---

mkdir src\app\posts\state
for %n in (src/app/posts/state/posts.actions.ts,src/app/posts/state/posts.effects.ts,src/app/posts/state/posts.reducer.ts,src/app/posts/state/posts.selector.ts,src/app/posts/state/posts.state.ts) do call >> %n
