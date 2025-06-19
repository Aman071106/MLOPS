#### 1. 💡 You’re Not Sharing Just Code — You’re Sharing:
- Your OS version (Linux base image)

- Programming language and version (Python 3.10, Node 20, etc.)

- All packages and dependencies (pip, npm, etc.)

- Config files

- Even your test tools (like pytest, curl, Postman mocks, etc.


#### 2. 🤔 What is QA?
- QA (Quality Assurance) = making sure your app:

- Works correctly ✅

- Has no bugs 🐞

- Is tested before release 🚀

#### QA usually means running tests:

- Unit tests

- Integration tests

- UI tests

- Security scans

- Performance checks

#### 🧪 So What is QA in Docker?
- Running all your tests (QA checks) inside Docker containers.

#### Why?

- Because Docker ensures the same clean environment every time.

- QA teams don’t have to manually install anything.

- It reduces bugs caused by "it worked on my machine" issues.


#### 3. 🛠️ If You Make Changes to a Container — What Happens to the Image?
- 👉 The image stays the same.
- 👉 Only the container changes.

- 🔍 Why?

- A Docker image is read-only

- A container is a writable layer on top of that image

- When you run a container from an image, Docker creates a copy-on-write layer. Changes you make (like installing a package or editing a file) happen only inside the container.

#### 4. DockerHub
Docker Hub provides a vast library of pre-built images and resources, accelerating development workflows and reducing setup time. You can build upon pre-built images from Docker Hub and then use repositories to share and distribute your own images with your team or millions of other developers.