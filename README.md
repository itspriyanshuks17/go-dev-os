# Go Development OS (Docker Image)

This repository provides a **Docker-based Go Development OS** that comes pre-installed with **Golang, Git, and Vim**, allowing you to quickly set up a coding environment for Go development.

## **Features**
- Pre-installed **Go** for development
- Includes **Git** for version control
- **Vim** for basic code editing
- Based on a lightweight **Debian** image

---

## **1. Building the Go Development OS Image**

### **Clone the Repository**
```sh
git clone https://github.com/itspriyanshuks17/go-dev-os
cd go-dev-os
```

### **Build the Docker Image**
```sh
docker build -t go-dev-os:latest .
```

If you want to publish it under your Docker Hub account:
```sh
docker tag go-dev-os:latest yourdockerhubusername/go-dev-os:latest
```

### **Push to Docker Hub (Optional)**
```sh
docker push yourdockerhubusername/go-dev-os:latest
```

---

## **2. Using the Go Development OS Image**

### **Pull the Image from Docker Hub**
```sh
docker pull yourdockerhubusername/go-dev-os:latest
```

### **Run the Container**
Start an interactive container where you can write and run Go code:
```sh
docker run -it --rm yourdockerhubusername/go-dev-os:latest
```

### **Mount a Local Directory for Persistent Storage**
To save your code outside the container:
```sh
docker run -it --rm -v $(pwd):/workspace yourdockerhubusername/go-dev-os:latest
```
This mounts your current directory to `/workspace` inside the container.

### **Running a Go Web Server (Example)**
If you're running a Go web application, expose a port:
```sh
docker run -it --rm -p 8080:8080 yourdockerhubusername/go-dev-os:latest
```

Inside the container, create a `server.go` file:
```go
package main

import (
	"fmt"
	"net/http"
)

func handler(w http.ResponseWriter, r *http.Request) {
	fmt.Fprintf(w, "Hello from Go in Docker!")
}

func main() {
	http.HandleFunc("/", handler)
	fmt.Println("Server running on port 8080...")
	http.ListenAndServe(":8080", nil)
}
```
Run it:
```sh
go run server.go
```
Now, open **http://localhost:8080** in your browser.

### **Running the Container in Detached Mode**
To keep the container running in the background:
```sh
docker run -d -p 8080:8080 --name go-container yourdockerhubusername/go-dev-os:latest
```
To stop it later:
```sh
docker stop go-container
```

### **Access Running Container**
If the container is running in the background:
```sh
docker exec -it go-container bash
```

---

## **3. Summary of Key Commands**
| Action | Command |
|--------|---------|
| Build the image | `docker build -t go-dev-os:latest .` |
| Push to Docker Hub | `docker push yourdockerhubusername/go-dev-os:latest` |
| Pull the image | `docker pull yourdockerhubusername/go-dev-os:latest` |
| Run interactive shell | `docker run -it --rm yourdockerhubusername/go-dev-os:latest` |
| Mount local directory | `docker run -it --rm -v $(pwd):/workspace yourdockerhubusername/go-dev-os:latest` |
| Run with port | `docker run -it --rm -p 8080:8080 yourdockerhubusername/go-dev-os:latest` |
| Run in detached mode | `docker run -d -p 8080:8080 --name go-container yourdockerhubusername/go-dev-os:latest` |
| Stop container | `docker stop go-container` |
| Access running container | `docker exec -it go-container bash` |

---

## **4. Contributing**
Feel free to fork this repository, open issues, or submit pull requests for improvements!

---

## **5. License**
This project is not licensed.

---

### **Happy Coding with Go! 🚀**

