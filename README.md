
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>LearnHub - Free Online Courses</title>

  <style>
    * {
      margin: 0;
      padding: 0;
      box-sizing: border-box;
    }

    body {
      font-family: Arial, sans-serif;
      background: #f5f7ff;
      color: #222;
      line-height: 1.6;
    }

    header {
      background: #5145cd;
      color: white;
      padding: 18px 8%;
      display: flex;
      justify-content: space-between;
      align-items: center;
      flex-wrap: wrap;
      gap: 12px;
    }

    header h2 { font-size: 26px; }

    nav a {
      color: white;
      text-decoration: none;
      margin-left: 18px;
    }

    .hero {
      text-align: center;
      padding: 65px 20px;
      background: linear-gradient(135deg, #5145cd, #8b5cf6);
      color: white;
    }

    .hero h1 {
      font-size: clamp(30px, 5vw, 46px);
      margin-bottom: 12px;
    }

    .hero p { margin-bottom: 24px; }

    .search {
      padding: 13px;
      width: min(90%, 420px);
      border: none;
      border-radius: 8px;
      font-size: 16px;
    }

    .courses {
      padding: 40px 8%;
      text-align: center;
    }

    .courses h2 {
      font-size: 30px;
      margin-bottom: 25px;
    }

    .course-list {
      display: grid;
      grid-template-columns: repeat(auto-fit, minmax(220px, 1fr));
      gap: 22px;
      text-align: left;
    }

    .card {
      background: white;
      padding: 24px;
      border-radius: 14px;
      box-shadow: 0 4px 15px #00000012;
      transition: transform 0.2s;
    }

    .card:hover { transform: translateY(-5px); }

    .emoji { font-size: 42px; }

    .card h3 {
      margin: 10px 0;
      color: #5145cd;
    }

    .category {
      color: #666;
      font-size: 13px;
    }

    .card p { margin: 10px 0; }

    button {
      background: #5145cd;
      color: white;
      border: none;
      border-radius: 7px;
      padding: 11px 17px;
      cursor: pointer;
      margin-top: 10px;
      font-size: 15px;
    }

    button:hover { background: #392eaa; }

    #message {
      margin: 20px 0;
      color: #247b45;
      font-weight: bold;
    }

    footer {
      background: #201c42;
      color: white;
      text-align: center;
      padding: 22px;
      margin-top: 20px;
    }

    @media (max-width: 480px) {
      header { justify-content: center; }
      nav a { margin: 0 7px; }
      .courses { padding: 30px 5%; }
    }
  </style>
</head>

<body>
  <header>
    <h2>📚 LearnHub</h2>
    <nav>
      <a href="#home">Home</a>
      <a href="#courses">Courses</a>
      <a href="#contact">Contact</a>
    </nav>
  </header>

  <section class="hero" id="home">
    <h1>Learn New Skills Online</h1>
    <p>Explore free courses and start building your future today!</p>
    <input
      class="search"
      id="search"
      type="search"
      placeholder="Search courses..."
      aria-label="Search courses"
    >
  </section>

  <main class="courses" id="courses">
    <h2>Our Free Courses</h2>
    <div class="course-list" id="courseList"></div>
    <p id="message" aria-live="polite"></p>
  </main>

  <footer id="contact">
    <p>Contact: learnhub@example.com</p>
    <p>© 2026 LearnHub | Learn. Practice. Grow.</p>
  </footer>

  <script>
    const courses = [
      {
        name: "HTML & CSS",
        icon: "🌐",
        category: "Web Development",
        duration: "4 weeks",
        description: "Build beautiful and responsive websites."
      },
      {
        name: "JavaScript",
        icon: "⚡",
        category: "Programming",
        duration: "6 weeks",
        description: "Add interactive features to your websites."
      },
      {
        name: "Python",
        icon: "🐍",
        category: "Programming",
        duration: "6 weeks",
        description: "Learn coding, loops, functions and logic."
      },
      {
        name: "React",
        icon: "⚛️",
        category: "Frontend Development",
        duration: "5 weeks",
        description: "Create modern user interfaces with React."
      },
      {
        name: "Java",
        icon: "☕",
        category: "Programming",
        duration: "8 weeks",
        description: "Learn object-oriented programming basics."
      },
      {
        name: "SQL & DBMS",
        icon: "🗄️",
        category: "Database",
        duration: "4 weeks",
        description: "Learn databases, queries and data management."
      }
    ];

    const courseList = document.getElementById("courseList");
    const search = document.getElementById("search");
    const message = document.getElementById("message");

    function displayCourses(items) {
      courseList.innerHTML = "";

      if (items.length === 0) {
        courseList.innerHTML = "<p>No courses found. Try another search.</p>";
        return;
      }

      items.forEach(course => {
        const card = document.createElement("article");
        card.className = "card";

        const icon = document.createElement("div");
        icon.className = "emoji";
        icon.textContent = course.icon;

        const title = document.createElement("h3");
        title.textContent = course.name;

        const category = document.createElement("div");
        category.className = "category";
        category.textContent = course.category;

        const description = document.createElement("p");
        description.textContent = course.description;

        const duration = document.createElement("p");
        duration.textContent = "Duration: " + course.duration;

        const button = document.createElement("button");
        button.textContent = "Enroll Now";

        button.addEventListener("click", () => {
          message.textContent =
            "You selected " + course.name +
            ". Enrollment demo successful!";
        });

        card.append(icon, title, category, description,
                    duration, button);
        courseList.appendChild(card);
      });
    }

    search.addEventListener("input", () => {
      const query = search.value.toLowerCase();

      const filtered = courses.filter(course =>
        course.name.toLowerCase().includes(query) ||
        course.category.toLowerCase().includes(query)
      );

      message.textContent = "";
      displayCourses(filtered);
    });

    displayCourses(courses);
  </script>
</body>
</html>
[proxispeak_server_code.pdf](https://github.com/user-attachments/files/33566462/proxispeak_server_code.pdf)
