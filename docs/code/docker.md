https://www.programiz.com/python-programming/online-compiler/

https://www.online-python.com/

https://www.h-schmidt.net/FloatConverter/IEEE754de.html

https://websim.com/@Nokix/datentyp-explorer-byte-short-int-long


Wo kann ich mich bewerben?
 
Eine direkte Bewerbung als "DAU" gibt es in der Regel nicht. Sie bewerben sich als Tester auf Plattformen oder bei Unternehmen, die explizit die DAU-Perspektive benötigen.
 
A) Bewerbung über Usability-Plattformen (Empfohlen für Quereinsteiger):
 
Dies ist der einfachste Weg, um als ungeschulter Tester (im Sinne des DAU) Aufträge zu erhalten.
RapidUsertests
TestingTime
Testbirds (Crowdtesting)
utest
Hier registrieren Sie sich als Tester. Sie werden dann per E-Mail eingeladen, Tests für Apps, Websites oder Prototypen durchzuführen. Ihre Vergütung erfolgt pro abgeschlossenem Test.
 
B) Bewerbung als (manueller) Software Tester:
 
Hierfür werden oft formellere Kriterien wie eine Ausbildung oder Zertifizierungen (z. B. ISTQB) verlangt, aber gerade für manuelle Tests ist eine intuitive, nicht-technische Perspektive sehr wertvoll.
Suchen Sie auf Jobportalen (LinkedIn, StepStone, Indeed) nach:
"Manueller Tester"
"Quality Assurance Tester (QA)"
"Software Tester Quereinsteiger"
 
Fazit
 
Wenn Sie die Rolle des DAU einnehmen möchten, melden Sie sich am besten bei den unter Abschnitt A genannten Usability- und Crowdtesting-Plattformen an. Dort ist die "Qualifikation", nicht vom Fach zu sein, explizit erwünscht.



https://www.youtube.com/watch?v=eelvWAURfdI&pp=ygURY29tcHV0ZXJwaGlsZSBvc2k%3D

checken - Linux befehle

hostnamectl
df -h
htop

dpkg -l

Linux commands cheatsheet
https://linux-commands.labex.io/

https://devhints.io/bash


Docker sortiert von Ende zu Anfang

Notiere den Befehl, um ein nginx-Image mit der Version 1:27 zu starten. Der Container soll im Hintergrund laufen, den Port 80 des Containers auf den Port 300 des Host-Systems mappen.
docker run -d -p 300:80 nginx: 1.27

https://forms.office.com/Pages/ResponsePage.aspx?id=RH-ZP46Zq0CoFE22ZxLIN9O_O_Ei1u9Cg_ofZATLLBBURDZNTU5GVUs0NDIwUkw3QTlTTFFNR0JSRC4u

https://qualidy.github.io/wiki-docker/content/devcontainer/
Devcontainer - Dockerschulung
 

 backend/src/mysite/main.py
 
# Importieren der Hauptklasse um die Webanwendung zu erstellen und eine Klasse zur kontrollierten Bhandlung von Fehlermeldungen:
from fastapi import FastAPI, HTTPException
# Basis für die Datenmodelle (Validierung):
from pydantic import BaseModel
 
# Der Einstiegspunkt:
app = FastAPI()
 
# Beschreibt ein vollständiges To-do-Objekt mit ID und Inhalt:
class TodoItem(BaseModel):
    id: int
    content: str
 
# beschreibt nur den Inhalt eines neuen To-do:
class TodoItemCreate(BaseModel):
    content: str
 
# Eine einfache Python-Liste, die alle Aufgaben enthält:
todos: list[TodoItem] = []
# Eine Zählvariable, um jedem Todo eine eindeutige ID zu geben:
id_counter = 1
 
@app.post("/todos", response_model=TodoItem)
async def create_todo(item: TodoItemCreate):
    global id_counter
    new_todo = TodoItem(id=id_counter, content=item.content)
    todos.append(new_todo)
    return new_todo
 
@app.get("/todos", response_model=list[TodoItem])
async def read_todos():
   return todos
 
@app.delete("/todos/{todo_id}")
async def delete_todo(todo_id: int):
    for index, todo in enumerate(todos):
        if todo.id == todo_id:
            todos.pop(index)
            return {"message": "Todo deleted successfully"}
    raise HTTPException(status_code=404, detail="Todo not found")
 
backend/dockerfile
 
FROM python:3.12-slim
 
WORKDIR /app
 
COPY requirements.txt requirements.txt
 
RUN pip install --no-cache-dir -r requirements.txt
 
COPY src/mysite mysite
 
EXPOSE 8000
 
CMD ["uvicorn", "mysite.main:app", "--host", "0.0.0.0", "--port", "8000"]
 
backend/requirements.txt
 
annotated-types==0.7.0
anyio==4.11.0
click==8.3.0
colorama==0.4.6
fastapi==0.118.1
h11==0.16.0
idna==3.10
pydantic==2.12.0
pydantic_core==2.41.1
sniffio==1.3.1
starlette==0.48.0
typing-inspection==0.4.2
typing_extensions==4.15.0
uvicorn==0.37.0
 
 
docker build -t todo-backend:0.4 backend
 
docker run -d --rm -p 8001:8000 todo-backend:0.4
 

 <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Minimal Todo List</title>
</head>
<body>
<h1>Todo List</h1>
<input type="text" id="newItem" placeholder="Enter a new item">
<button onclick="addItem()">Add</button>
<ul id="todoList"></ul>
 
    <script>
        const API_URL = 'http://localhost:8000';
 
        async function fetchTodos() {
            const response = await fetch(`${API_URL}/todos`);
            const todos = await response.json();
            const list = document.getElementById('todoList');
            list.innerHTML = '';
            todos.forEach(todo => {
                const li = document.createElement('li');
                li.textContent = todo.content;
                const deleteBtn = document.createElement('button');
                deleteBtn.textContent = 'Delete';
                deleteBtn.onclick = () => deleteItem(todo.id);
                li.appendChild(deleteBtn);
                list.appendChild(li);
            });
        }
 
        async function addItem() {
            const input = document.getElementById('newItem');
            if (input.value.trim() !== '') {
                const response = await fetch(`${API_URL}/todos`, {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json',
                    },
                    body: JSON.stringify({ content: input.value }),
                });
                if (response.ok) {
                    input.value = '';
                    fetchTodos();
                }
            }
        }
 
        async function deleteItem(id) {
            const response = await fetch(`${API_URL}/todos/${id}`, {
                method: 'DELETE',
            });
            if (response.ok) {
                fetchTodos();
            }
        }
 
        fetchTodos();
</script>
</body>
</html>

docker build -t todo-frontend:2.0 frontend

docker run -d --rm -p 500:80 todo-frontend:2.0

# Importieren der Hauptklasse um die Webanwendung zu erstellen und eine Klasse zur kontrollierten Bhandlung von Fehlermeldungen:
from fastapi import FastAPI, HTTPException
# Basis für die Datenmodelle (Validierung):
from pydantic import BaseModel
# CORS-Middleware importieren, um CORS-Fehler zu beheben:
from fastapi.middleware.cors import CORSMiddleware  
 
# Der Einstiegspunkt:
app = FastAPI()
 
# CORS zulassen:
app.add_middleware(
    CORSMiddleware,
    allow_origins=["http://localhost"],  # Hier die URL des Frontends
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
 
# Beschreibt ein vollständiges To-do-Objekt mit ID und Inhalt:
class TodoItem(BaseModel):
    id: int
    content: str
 
# beschreibt nur den Inhalt eines neuen To-do:
class TodoItemCreate(BaseModel):
    content: str
 
# Eine einfache Python-Liste, die alle Aufgaben enthält:
todos: list[TodoItem] = []
# Eine Zählvariable, um jedem Todo eine eindeutige ID zu geben:
id_counter = 1
 
@app.post("/todos", response_model=TodoItem)
async def create_todo(item: TodoItemCreate):
    global id_counter
    new_todo = TodoItem(id=id_counter, content=item.content)
    todos.append(new_todo)
    return new_todo
 
@app.get("/todos", response_model=list[TodoItem])
async def read_todos():
   return todos
 
@app.delete("/todos/{todo_id}")
async def delete_todo(todo_id: int):
    for index, todo in enumerate(todos):
        if todo.id == todo_id:
            todos.pop(index)
            return {"message": "Todo deleted successfully"}
    raise HTTPException(status_code=404, detail="Todo not found")

    docker build -t todo-backend:0.5 backend
 
docker run -d --rm -p 8001:8000 todo-backend:0.5
 
# Importieren der Hauptklasse um die Webanwendung zu erstellen und eine Klasse zur kontrollierten Bhandlung von Fehlermeldungen:
from fastapi import FastAPI, HTTPException
# Basis für die Datenmodelle (Validierung):
from pydantic import BaseModel
# CORS-Middleware importieren, um CORS-Fehler zu beheben:
from fastapi.middleware.cors import CORSMiddleware  
 
# Der Einstiegspunkt:
app = FastAPI()
 
origins = [
    "http://localhost",
    "http://localhost:80",
    "http://localhost:500",
    "http://127.0.0.1",
    "http://127.0.0.1:80",
    "http://127.0.0.1:500",
]
 
# CORS zulassen:
app.add_middleware(
    CORSMiddleware,
    allow_origins=origins,  # Hier die URL des Frontends
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
 
# Beschreibt ein vollständiges To-do-Objekt mit ID und Inhalt:
class TodoItem(BaseModel):
    id: int
    content: str
 
# beschreibt nur den Inhalt eines neuen To-do:
class TodoItemCreate(BaseModel):
    content: str
 
# Eine einfache Python-Liste, die alle Aufgaben enthält:
todos: list[TodoItem] = []
# Eine Zählvariable, um jedem Todo eine eindeutige ID zu geben:
id_counter = 1
 
@app.post("/todos", response_model=TodoItem)
async def create_todo(item: TodoItemCreate):
    global id_counter
    new_todo = TodoItem(id=id_counter, content=item.content)
    todos.append(new_todo)
    return new_todo
 
@app.get("/todos", response_model=list[TodoItem])
async def read_todos():
   return todos
 
@app.delete("/todos/{todo_id}")
async def delete_todo(todo_id: int):
    for index, todo in enumerate(todos):
        if todo.id == todo_id:
            todos.pop(index)
            return {"message": "Todo deleted successfully"}
    raise HTTPException(status_code=404, detail="Todo not found")
 
docker build -t todo-backend:0.6 backend
 

 docker-compose.yml

 services:
  backend:
    image: todo-backend:0.6
    pull_policy: never
    container_name: todo-backend-container
    build:
      context: ./backend
      dockerfile: dockerfile
    ports:
      - 8001:8000
 
  frontend:
    image: todo-frontend:2.0
    pull_policy: never
    container_name: todo-frontend-container
    build:
      context: ./frontend
      dockerfile: dockerfile
    ports:
      - 500:80
 
docker compose build
 
docker compose up
 
 write_in_file.py
 
f = 'data.txt'
open(f, 'a').write('Datei beschrieben!\n')
print(open(f).read())
 
 docker container prune

 docker run -v mydata:/data  python:latest python -c "f = 'data/data.txt'; open(f, 'a').write('Datei beschrieben!\n'); print(open(f).read())"

 docker run --rm -v mydata:/data  python:latest python -c "f = 'data/data.txt'; open(f, 'a').write('Datei beschrieben!\n'); print(open(f).read())"

 docker run --rm -v C:\my_bind_mount:/data  python:latest python -c "f = 'data/data.txt'; open(f, 'a').write('Datei beschrieben!\n'); print(open(f).read())"

 <!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8" />
<meta name="viewport" content="width=device-width, initial-scale=1.0"/>
<title>Frontend-only Todo List</title>
</head>
<body>
<h1>Todo List</h1>
<input type="text" id="newItem" placeholder="Enter a new item" />
<button onclick="addItem()">Add</button>
<ul id="todoList"></ul>
 
  <script>
    // In-Memory-Speicher für unsere Aufgaben
    let todos = [];
 
    function renderTodos() {
      const list = document.getElementById('todoList');
      list.innerHTML = '';
      todos.forEach((todo, index) => {
        const li = document.createElement('li');
        li.textContent = todo;
 
        const deleteBtn = document.createElement('button');
        deleteBtn.textContent = 'Delete';
        deleteBtn.onclick = () => {
          todos.splice(index, 1);
          renderTodos();
        };
 
        li.appendChild(deleteBtn);
        list.appendChild(li);
      });
    }
 
    function addItem() {
      const input = document.getElementById('newItem');
      const value = input.value.trim();
      if (value !== '') {
        todos.push(value);
        input.value = '';
        renderTodos();
      }
    }
 
    // Initialanzeige
    renderTodos();
</script>
</body>
</html>

docker build -t mytodo:1.0 frontend

docker run -d -p 100:80 mytodo:1.0

https://qualidy.github.io/wiki-docker/content/container_webinhalt_bearbeiten/

docker run -d --name web-server -p 8080:80 nginx:1.27.0

whoami
 
docker exec -it web-server sh

 https://qualidy.github.io/wiki-docker/content/container_webinhalt_bearbeiten/#hinweis-zu-persistenz

 https://hub.docker.com/

 https://hub.docker.com/r/dorowu/ubuntu-desktop-lxde-vnc

 docker run -p 6000:80 --name ubuntu-desktop dorowu/ubuntu-desktop-lxde-vnc

 <!DOCTYPE html>
<html>
<head>
<title>Welcome to nginx!</title>
<style>
html { color-scheme: light dark; }
body { width: 35em; margin: 0 auto;
font-family: Tahoma, Verdana, Arial, sans-serif; }
</style>
</head>
<body>
<h1>Willkommen im Dockerunterricht!</h1>
<p>Hier lernst du alles, was du nie wissen wolltest.</p>
<br/>
<p>WOW!</p>
</body>
</html>

FROM nginx:alpine
 
COPY index.html /usr/share/nginx/html/index.html
 
RUN chown nginx:nginx /usr/share/nginx/html/index.html

docker build -t meine-website:1.0 .

https://app.docker.com/signup

https://dashboard.render.com/login

https://hub.docker.com/r/viktorreichert/meine-website

https://qualidy.github.io/wiki-docker/content/host/#5-docker-image-bei-render-hosten-web-service


docker rm $(docker ps -q -a)

docker stop $(docker ps -q)

https://excalidraw.com/#room=b0e7e367f45af373a6fd,KaEHXR3Zv450Y1F9ZLHT9w

Continous Integration / Continous Delivery  CI/CD