 <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Jyothi Education College Portal</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.6.0/css/all.min.css">
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap');
        body { font-family: 'Inter', sans-serif; }
        .nav-active { @apply bg-blue-600 text-white; }
        .card-hover:hover { transform: translateY(-4px); }
    </style>
</head>
<body class="bg-gray-50">

    <!-- Login Page -->
    <div id="login-page" class="min-h-screen flex items-center justify-center bg-gradient-to-br from-blue-700 to-indigo-800">
        <div class="bg-white rounded-3xl shadow-2xl w-full max-w-md p-10">
            <div class="text-center mb-8">
                <div class="w-16 h-16 mx-auto bg-blue-600 rounded-2xl flex items-center justify-center text-white text-4xl font-bold mb-4">JEC</div>
                <h1 class="text-3xl font-bold text-gray-900">Jyothi Education College</h1>
                <p class="text-gray-500 mt-1">Student Portal</p>
            </div>

            <div class="space-y-6">
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Student ID</label>
                    <input id="student-id" type="text" placeholder="e.g. 245280479" 
                           class="w-full px-5 py-4 border border-gray-300 rounded-2xl focus:outline-none focus:border-blue-500">
                </div>
                <div>
                    <label class="block text-sm font-medium text-gray-700 mb-2">Password</label>
                    <input id="password" type="password" placeholder="Enter Password" 
                           class="w-full px-5 py-4 border border-gray-300 rounded-2xl focus:outline-none focus:border-blue-500">
                </div>

                <button onclick="login()" 
                        class="w-full py-4 bg-blue-600 hover:bg-blue-700 text-white font-semibold rounded-2xl text-lg">
                    Login
                </button>
                <p class="text-center text-sm text-gray-500">Demo: Use any password</p>
            </div>
        </div>
    </div>

    <!-- Main Portal -->
    <div id="main-portal" class="hidden flex min-h-screen">
        <!-- Sidebar -->
        <div class="w-72 bg-white border-r flex flex-col">
            <div class="p-6 border-b">
                <div class="flex items-center gap-3">
                    <div class="w-12 h-12 bg-blue-600 rounded-2xl flex items-center justify-center text-white text-3xl font-bold">JEC</div>
                    <div>
                        <h1 class="text-2xl font-bold tracking-tight">Jyothi Education</h1>
                        <p class="text-xs text-gray-500">College Portal</p>
                    </div>
                </div>
            </div>

            <nav class="flex-1 p-4 space-y-1 overflow-auto">
                <a onclick="showSection('dashboard')" class="nav-link flex items-center gap-3 px-5 py-4 rounded-2xl cursor-pointer nav-active" id="nav-dashboard">
                    <i class="fa-solid fa-house"></i> Dashboard
                </a>
                <a onclick="showSection('profile')" class="nav-link flex items-center gap-3 px-5 py-4 rounded-2xl cursor-pointer" id="nav-profile">
                    <i class="fa-solid fa-user"></i> Profile
                </a>
                <a onclick="showSection('attendance')" class="nav-link flex items-center gap-3 px-5 py-4 rounded-2xl cursor-pointer" id="nav-attendance">
                    <i class="fa-solid fa-calendar-check"></i> Attendance
                </a>
                <a onclick="showSection('marks')" class="nav-link flex items-center gap-3 px-5 py-4 rounded-2xl cursor-pointer" id="nav-marks">
                    <i class="fa-solid fa-graduation-cap"></i> Marks
                </a>
                <a onclick="showSection('fees')" class="nav-link flex items-center gap-3 px-5 py-4 rounded-2xl cursor-pointer" id="nav-fees">
                    <i class="fa-solid fa-money-bill"></i> Fees
                </a>
                <a onclick="showSection('courses')" class="nav-link flex items-center gap-3 px-5 py-4 rounded-2xl cursor-pointer" id="nav-courses">
                    <i class="fa-solid fa-book"></i> Online Courses
                </a>
                <a onclick="showSection('complaints')" class="nav-link flex items-center gap-3 px-5 py-4 rounded-2xl cursor-pointer" id="nav-complaints">
                    <i class="fa-solid fa-exclamation-triangle"></i> Complaints
                </a>
            </nav>

            <div class="p-4 border-t mt-auto">
                <div class="flex items-center gap-3 p-3 bg-gray-50 rounded-2xl">
                    <div class="w-10 h-10 bg-blue-100 rounded-2xl flex items-center justify-center text-blue-600 font-bold text-xl">👤</div>
                    <div>
                        <p class="font-semibold text-sm" id="sidebar-name">Rajsekhar</p>
                        <p class="text-xs text-gray-500" id="sidebar-id">245280479</p>
                    </div>
                </div>
                <button onclick="logout()" class="mt-6 w-full text-red-600 hover:bg-red-50 py-3 rounded-2xl flex items-center justify-center gap-2">
                    <i class="fa-solid fa-right-from-bracket"></i> Logout
                </button>
            </div>
        </div>

        <!-- Main Content -->
        <div class="flex-1 overflow-auto">
            <header class="bg-white border-b px-8 py-5 flex justify-between items-center sticky top-0 z-50">
                <h1 class="text-2xl font-semibold text-gray-800" id="page-title">Dashboard</h1>
                <div class="flex items-center gap-4">
                    <div class="text-right">
                        <p class="font-medium" id="header-name">Rajsekhar</p>
                        <p class="text-xs text-gray-500" id="header-id">245280479</p>
                    </div>
                </div>
            </header>

            <!-- Dashboard -->
            <div id="section-dashboard" class="p-8">
                <div class="grid grid-cols-1 md:grid-cols-4 gap-6">
                    <div class="bg-white p-6 rounded-3xl shadow-sm">
                        <p class="text-gray-500">Attendance</p>
                        <p class="text-5xl font-bold text-blue-600 mt-2">94%</p>
                    </div>
                    <div class="bg-white p-6 rounded-3xl shadow-sm">
                        <p class="text-gray-500">CGPA</p>
                        <p class="text-5xl font-bold text-purple-600 mt-2">8.9</p>
                    </div>
                    <div class="bg-white p-6 rounded-3xl shadow-sm">
                        <p class="text-gray-500">Fees Due</p>
                        <p class="text-5xl font-bold text-orange-600 mt-2">₹8,500</p>
                    </div>
                    <div class="bg-white p-6 rounded-3xl shadow-sm">
                        <p class="text-gray-500">Courses Enrolled</p>
                        <p class="text-5xl font-bold text-emerald-600 mt-2">7</p>
                    </div>
                </div>

                <div class="mt-8 bg-white rounded-3xl p-6">
                    <h2 class="font-semibold mb-4">Quick Links</h2>
                    <div class="grid grid-cols-2 md:grid-cols-4 gap-4">
                        <div onclick="showSection('courses')" class="cursor-pointer bg-gradient-to-br from-blue-50 to-cyan-50 p-6 rounded-3xl text-center card-hover">
                            <i class="fa-solid fa-book text-4xl text-blue-600 mb-3"></i>
                            <p class="font-medium">Online Courses</p>
                        </div>
                        <div onclick="showSection('attendance')" class="cursor-pointer bg-gradient-to-br from-emerald-50 to-teal-50 p-6 rounded-3xl text-center card-hover">
                            <i class="fa-solid fa-calendar-check text-4xl text-emerald-600 mb-3"></i>
                            <p class="font-medium">Attendance</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Profile -->
            <div id="section-profile" class="p-8 hidden">
                <div class="bg-white rounded-3xl p-8 max-w-3xl">
                    <h2 class="text-2xl font-bold mb-8">Student Profile</h2>
                    <div class="space-y-4 text-lg">
                        <p><strong>Name:</strong> <span id="profile-name">Rajsekhar</span></p>
                        <p><strong>Student ID:</strong> <span id="profile-id">245280479</span></p>
                        <p><strong>Course:</strong> B.Tech - Computer Science</p>
                        <p><strong>Year:</strong> 3rd Year</p>
                        <p><strong>Email:</strong> student@jec.edu.in</p>
                    </div>
                </div>
            </div>

            <!-- Attendance -->
            <div id="section-attendance" class="p-8 hidden">
                <div class="bg-white rounded-3xl p-8">
                    <h2 class="text-2xl font-semibold mb-6">Attendance Record</h2>
                    <table class="w-full text-sm">
                        <thead class="bg-gray-100">
                            <tr>
                                <th class="text-left p-4">Subject</th>
                                <th class="text-center p-4">Total</th>
                                <th class="text-center p-4">Present</th>
                                <th class="text-center p-4">Percentage</th>
                            </tr>
                        </thead>
                        <tbody id="attendance-body" class="divide-y"></tbody>
                    </table>
                </div>
            </div>

            <!-- Marks -->
            <div id="section-marks" class="p-8 hidden">
                <div class="bg-white rounded-3xl p-8">
                    <h2 class="text-2xl font-semibold mb-6">Semester Marks</h2>
                    <table class="w-full text-sm">
                        <thead class="bg-gray-100">
                            <tr>
                                <th class="text-left p-4">Subject</th>
                                <th class="text-center p-4">Internal</th>
                                <th class="text-center p-4">External</th>
                                <th class="text-center p-4">Total</th>
                                <th class="text-center p-4">Grade</th>
                            </tr>
                        </thead>
                        <tbody id="marks-body" class="divide-y"></tbody>
                    </table>
                </div>
            </div>

            <!-- Fees -->
            <div id="section-fees" class="p-8 hidden">
                <div class="bg-white rounded-3xl p-8 max-w-lg">
                    <h2 class="text-2xl font-semibold mb-6">Fee Details</h2>
                    <div class="space-y-6">
                        <div class="flex justify-between border-b pb-6">
                            <div>
                                <p class="font-medium">Semester Tuition Fee</p>
                                <p class="text-sm text-gray-500">Due: 30 June 2026</p>
                            </div>
                            <div class="text-right">
                                <p class="font-bold text-xl">₹25,000</p>
                                <span class="text-orange-600">Pending</span>
                            </div>
                        </div>
                        <button class="w-full py-4 bg-green-600 text-white rounded-2xl font-medium">Pay Now</button>
                    </div>
                </div>
            </div>

            <!-- Courses -->
            <div id="section-courses" class="p-8 hidden">
                <h2 class="text-2xl font-semibold mb-6 px-8">Online Learning Portals</h2>
                <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-6 px-8">
                    <div class="bg-white rounded-3xl p-6 card-hover">
                        <div class="h-40 bg-gradient-to-br from-blue-500 to-cyan-400 rounded-2xl flex items-center justify-center text-white text-6xl mb-4">🐍</div>
                        <h3 class="font-semibold text-xl">Python Programming</h3>
                        <button onclick="enrollCourse(this)" class="mt-6 w-full py-3 bg-blue-600 text-white rounded-2xl">Enroll / Continue</button>
                    </div>
                    <div class="bg-white rounded-3xl p-6 card-hover">
                        <div class="h-40 bg-gradient-to-br from-red-500 to-orange-400 rounded-2xl flex items-center justify-center text-white text-6xl mb-4">☕</div>
                        <h3 class="font-semibold text-xl">Java Programming</h3>
                        <button onclick="enrollCourse(this)" class="mt-6 w-full py-3 bg-blue-600 text-white rounded-2xl">Enroll / Continue</button>
                    </div>
                    <div class="bg-white rounded-3xl p-6 card-hover">
                        <div class="h-40 bg-gradient-to-br from-purple-500 to-violet-400 rounded-2xl flex items-center justify-center text-white text-6xl mb-4">C++</div>
                        <h3 class="font-semibold text-xl">C++ Programming</h3>
                        <button onclick="enrollCourse(this)" class="mt-6 w-full py-3 bg-blue-600 text-white rounded-2xl">Enroll / Continue</button>
                    </div>
                    <div class="bg-white rounded-3xl p-6 card-hover">
                        <div class="h-40 bg-gradient-to-br from-emerald-500 to-teal-400 rounded-2xl flex items-center justify-center text-white text-6xl mb-4">🌐</div>
                        <h3 class="font-semibold text-xl">HTML & Web Design</h3>
                        <button onclick="enrollCourse(this)" class="mt-6 w-full py-3 bg-blue-600 text-white rounded-2xl">Enroll / Continue</button>
                    </div>
                </div>
            </div>

            <!-- Complaints -->
            <div id="section-complaints" class="p-8 hidden">
                <div class="max-w-2xl mx-auto bg-white rounded-3xl p-8">
                    <h2 class="text-2xl font-semibold mb-6">Raise a Complaint</h2>
                    <textarea id="complaint-text" rows="5" class="w-full border rounded-3xl p-6 focus:outline-none" placeholder="Describe your issue..."></textarea>
                    <button onclick="submitComplaint()" class="mt-6 w-full py-4 bg-red-600 hover:bg-red-700 text-white rounded-3xl font-medium">Submit Complaint</button>

                    <h3 class="font-medium mt-12 mb-4">Previous Complaints</h3>
                    <div id="complaint-list" class="space-y-4"></div>
                </div>
            </div>
        </div>
    </div>

    <!-- Toast -->
    <div id="toast" class="hidden fixed bottom-6 right-6 bg-gray-900 text-white px-6 py-4 rounded-3xl shadow-2xl flex items-center gap-3">
        <span id="toast-text"></span>
    </div>

    <script>
        // Students Database
        const students = {
            "245280479": { name: "Rajsekhar" },
            "245280467": { name: "Nikitha" },
            "2452890565": { name: "Allogolu Sagar" },
            "2452890376": { name: "Chinni Krishna" },
            "2452890324": { name: "Lahari" },
            "2453890687": { name: "Gayatri" },
            "2453890123": { name: "Ranjitha" },
            "2452890476": { name: "Jatin Paul" }   // Newly Added
        };

        let currentStudent = null;

        const attendanceData = [
            {sub: "Python Programming", total: 45, present: 43, perc: 95},
            {sub: "Data Structures", total: 40, present: 37, perc: 92},
            {sub: "Web Development", total: 38, present: 36, perc: 94}
        ];

        const marksData = [
            {sub: "Python Programming", int: 28, ext: 65, total: 93, grade: "A+"},
            {sub: "Data Structures", int: 25, ext: 58, total: 83, grade: "A"}
        ];

        let complaints = [];

        function login() {
            const idInput = document.getElementById('student-id').value.trim();
            if (!idInput || !students[idInput]) {
                showToast("Invalid Student ID", true);
                return;
            }

            currentStudent = students[idInput];

            document.getElementById('login-page').classList.add('hidden');
            document.getElementById('main-portal').classList.remove('hidden');

            // Update names and IDs
            document.getElementById('header-name').textContent = currentStudent.name;
            document.getElementById('header-id').textContent = idInput;
            document.getElementById('sidebar-name').textContent = currentStudent.name;
            document.getElementById('sidebar-id').textContent = idInput;
            document.getElementById('profile-name').textContent = currentStudent.name;
            document.getElementById('profile-id').textContent = idInput;

            showSection('dashboard');
            showToast(`Welcome, ${currentStudent.name}!`);
        }

        function showSection(section) {
            document.querySelectorAll('[id^="section-"]').forEach(el => el.classList.add('hidden'));
            document.getElementById(`section-${section}`).classList.remove('hidden');

            document.querySelectorAll('.nav-link').forEach(link => link.classList.remove('nav-active'));
            document.getElementById(`nav-${section}`).classList.add('nav-active');

            document.getElementById('page-title').textContent = 
                section === 'dashboard' ? 'Dashboard' :
                section === 'profile' ? 'My Profile' :
                section === 'attendance' ? 'Attendance' :
                section === 'marks' ? 'Academic Marks' :
                section === 'fees' ? 'Fee Details' :
                section === 'courses' ? 'Online Courses' : 'Complaints';
        }

        function renderAttendance() {
            const tbody = document.getElementById('attendance-body');
            tbody.innerHTML = attendanceData.map(a => `
                <tr>
                    <td class="p-4">${a.sub}</td>
                    <td class="text-center p-4">${a.total}</td>
                    <td class="text-center p-4">${a.present}</td>
                    <td class="text-center p-4 font-semibold text-emerald-600">${a.perc}%</td>
                </tr>
            `).join('');
        }

        function renderMarks() {
            const tbody = document.getElementById('marks-body');
            tbody.innerHTML = marksData.map(m => `
                <tr>
                    <td class="p-4">${m.sub}</td>
                    <td class="text-center p-4">${m.int}</td>
                    <td class="text-center p-4">${m.ext}</td>
                    <td class="text-center p-4 font-bold">${m.total}</td>
                    <td class="text-center p-4"><span class="bg-emerald-100 text-emerald-700 px-4 py-1 rounded-3xl text-sm">${m.grade}</span></td>
                </tr>
            `).join('');
        }

        function enrollCourse(btn) {
            btn.textContent = "✅ Enrolled";
            btn.disabled = true;
            showToast("Course enrolled successfully!");
        }

        function submitComplaint() {
            const text = document.getElementById('complaint-text').value.trim();
            if (!text) return showToast("Please write your complaint", true);

            complaints.unshift({
                date: new Date().toLocaleDateString(),
                text: text,
                status: "Pending"
            });

            renderComplaints();
            document.getElementById('complaint-text').value = '';
            showToast("Complaint submitted successfully!");
        }

        function renderComplaints() {
            const container = document.getElementById('complaint-list');
            container.innerHTML = complaints.map(c => `
                <div class="border rounded-2xl p-5">
                    <p class="text-xs text-gray-500">${c.date} • ${c.status}</p>
                    <p class="mt-2">${c.text}</p>
                </div>
            `).join('');
        }

        function showToast(msg, error = false) {
            const toast = document.getElementById('toast');
            document.getElementById('toast-text').textContent = msg;
            if (error) toast.classList.add('bg-red-600');
            else toast.classList.remove('bg-red-600');
            toast.classList.remove('hidden');
            setTimeout(() => toast.classList.add('hidden'), 3000);
        }

        function logout() {
            if (confirm("Logout from portal?")) {
                document.getElementById('main-portal').classList.add('hidden');
                document.getElementById('login-page').classList.remove('hidden');
                document.getElementById('student-id').value = '';
            }
        }

        // Initialize
        window.onload = () => {
            document.getElementById('student-id').value = "245280479";
            renderAttendance();
            renderMarks();
            renderComplaints();
        };
    </script>
</body>
</html>
