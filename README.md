<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Google Data Analytics: 6-Week Fast-Track Sprint</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link href="https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;500;700;900&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Roboto', sans-serif;
            background-color: #F3F4F6; /* Gray 100 */
        }
        
        /* Chart Container Styling - Mandatory Requirement */
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px; /* Max width constraint */
            margin-left: auto;
            margin-right: auto;
            height: 350px; /* Base height */
            max-height: 400px;
        }

        @media (min-width: 768px) {
            .chart-container {
                height: 400px;
            }
        }

        /* Timeline Connector Logic using CSS Borders */
        .timeline-line {
            position: absolute;
            left: 24px;
            top: 0;
            bottom: 0;
            width: 4px;
            background-color: #3B82F6; /* Blue 500 */
            z-index: 0;
        }
        
        .timeline-item:last-child .timeline-line {
            display: none;
        }

        /* Palette Classes */
        .text-brand-blue { color: #2563EB; }
        .bg-brand-blue { background-color: #2563EB; }
        .text-brand-purple { color: #7C3AED; }
        .bg-brand-purple { background-color: #7C3AED; }
        .text-brand-amber { color: #D97706; }
        .bg-brand-amber { background-color: #F59E0B; }

        .gemini-gradient {
            background: linear-gradient(90deg, #4285F4, #9B72CB, #D96570);
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
        }
    </style>
    <!-- 
        Palette Selection: "Electric Productivity"
        Primary: Blue (#2563EB)
        Secondary: Purple (#7C3AED)
        Accent: Amber (#F59E0B)
        Base: Gray/White
        
        Plan Summary:
        1. Intro: Hook about the 6-week sprint.
        2. Overview: Charts showing curriculum balance and effort.
        3. Weekly Roadmap: Detailed HTML-based timeline.
        4. Strategy: Daily breakdown.
        5. ✨ Gemini Integrations: Project Generator, Study Guide, Quiz Master.
        
        No SVG. No Mermaid.
    -->
</head>
<body class="text-gray-800">

    <!-- Header Section -->
    <header class="bg-gradient-to-r from-blue-700 to-indigo-800 text-white shadow-lg">
        <div class="container mx-auto px-6 py-12 text-center">
            <h1 class="text-4xl md:text-6xl font-black mb-4 tracking-tight">The 6-Week Sprint</h1>
            <p class="text-xl md:text-2xl font-light text-blue-100 max-w-3xl mx-auto">
                Fast-track your Google Advanced Data Analytics Certification for March placements.
                <br>
                <span class="font-bold text-yellow-400">Zero to Hero in 42 Days.</span>
            </p>
        </div>
    </header>

    <!-- Main Content Grid -->
    <main class="container mx-auto px-4 py-10 space-y-16">

        <!-- Section: AI Learning Assistant -->
        <section class="bg-white rounded-2xl shadow-xl overflow-hidden border border-purple-100">
            <div class="bg-gradient-to-r from-purple-50 to-blue-50 px-8 py-6 border-b border-purple-100">
                <h2 class="text-2xl font-bold gemini-gradient">✨ AI Learning Assistant</h2>
                <p class="text-sm text-gray-600 mt-1">Use Gemini to accelerate your studies and build your portfolio faster.</p>
            </div>
            
            <div class="p-8 grid grid-cols-1 md:grid-cols-3 gap-8">
                <!-- Project Generator -->
                <div class="space-y-4">
                    <h3 class="font-bold text-gray-800 flex items-center">
                        <span class="text-xl mr-2">🚀</span> Portfolio Project Generator
                    </h3>
                    <p class="text-sm text-gray-600">Stuck on a capstone idea? Tell us your interest, and Gemini will build a project brief.</p>
                    <input id="interestInput" type="text" placeholder="e.g. Football, Finance, Gaming" class="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-purple-400 outline-none text-sm">
                    <button onclick="generateProject()" class="w-full bg-indigo-600 hover:bg-indigo-700 text-white py-2 rounded-lg font-bold text-sm transition-colors">✨ Generate Idea</button>
                    <div id="projectOutput" class="hidden text-xs p-3 bg-gray-50 rounded border italic text-gray-700 max-h-40 overflow-y-auto"></div>
                </div>

                <!-- Concept Explainer -->
                <div class="space-y-4">
                    <h3 class="font-bold text-gray-800 flex items-center">
                        <span class="text-xl mr-2">🧠</span> Concept "Cheat Sheet"
                    </h3>
                    <p class="text-sm text-gray-600">Confused by a stats or ML concept? Get a simple 1-minute summary.</p>
                    <input id="conceptInput" type="text" placeholder="e.g. P-Values, Random Forest" class="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-purple-400 outline-none text-sm">
                    <button onclick="explainConcept()" class="w-full bg-purple-600 hover:bg-purple-700 text-white py-2 rounded-lg font-bold text-sm transition-colors">✨ Simplify Now</button>
                    <div id="conceptOutput" class="hidden text-xs p-3 bg-gray-50 rounded border text-gray-700 max-h-40 overflow-y-auto"></div>
                </div>

                <!-- Quiz Master -->
                <div class="space-y-4">
                    <h3 class="font-bold text-gray-800 flex items-center">
                        <span class="text-xl mr-2">📝</span> Rapid Quiz Master
                    </h3>
                    <p class="text-sm text-gray-600">Quickly test your knowledge on any topic from the curriculum.</p>
                    <select id="topicSelect" class="w-full px-4 py-2 border rounded-lg focus:ring-2 focus:ring-purple-400 outline-none text-sm bg-white">
                        <option value="Python Data Structures">Python Data Structures</option>
                        <option value="Hypothesis Testing">Hypothesis Testing</option>
                        <option value="Logistic Regression">Logistic Regression</option>
                        <option value="Machine Learning Metrics">ML Metrics</option>
                    </select>
                    <button onclick="generateQuiz()" class="w-full bg-pink-600 hover:bg-pink-700 text-white py-2 rounded-lg font-bold text-sm transition-colors">✨ Start Quiz</button>
                    <div id="quizOutput" class="hidden text-xs p-3 bg-gray-50 rounded border text-gray-700 max-h-40 overflow-y-auto"></div>
                </div>
            </div>
            
            <div id="loadingIndicator" class="hidden px-8 py-2 bg-purple-600 text-white text-xs text-center animate-pulse">
                Gemini is thinking...
            </div>
        </section>

        <!-- Section 1: Strategic Overview -->
        <section>
            <div class="mb-8 text-center max-w-3xl mx-auto">
                <h2 class="text-3xl font-bold text-gray-900 mb-4 border-b-4 border-blue-500 inline-block pb-2">Strategic Overview</h2>
                <p class="text-gray-600 text-lg">
                    This isn't just a course; it's a tactical mission. By condensing a 6-month curriculum into 6 weeks, we prioritize high-impact skills like Python, Statistics, and Machine Learning. The charts below visualize the distribution of effort and the skills you will secure.
                </p>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
                <!-- Chart 1: Curriculum Composition -->
                <div class="bg-white rounded-xl shadow-md p-6">
                    <h3 class="text-xl font-bold text-gray-800 mb-2">Curriculum Focus Areas</h3>
                    <p class="text-sm text-gray-500 mb-4">
                        We shift focus heavily towards technical implementation. While foundations are important, the bulk of your time (and interview questions) will come from the "Core Tech" sectors: Stats, Regression, and ML.
                    </p>
                    <div class="chart-container">
                        <canvas id="curriculumChart"></canvas>
                    </div>
                </div>

                <!-- Chart 2: Skill Radar -->
                <div class="bg-white rounded-xl shadow-md p-6">
                    <h3 class="text-xl font-bold text-gray-800 mb-2">Target Skill Profile</h3>
                    <p class="text-sm text-gray-500 mb-4">
                        By Week 6, your profile will transform. This radar chart benchmarks your expected proficiency in critical areas required for Tier-1 placements compared to a generalist.
                    </p>
                    <div class="chart-container">
                        <canvas id="skillsRadarChart"></canvas>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section 2: The Intensity Curve -->
        <section class="bg-blue-50 rounded-2xl p-8 shadow-inner">
            <div class="grid grid-cols-1 lg:grid-cols-3 gap-8 items-center">
                <div class="lg:col-span-1">
                    <h2 class="text-3xl font-bold text-gray-900 mb-4">The Effort Curve</h2>
                    <p class="text-gray-700 mb-6">
                        Not all weeks are created equal. The schedule starts with a manageable learning curve in Python basics, but quickly ramps up.
                    </p>
                    <div class="bg-white border-l-4 border-yellow-500 p-4 rounded shadow-sm">
                        <h4 class="font-bold text-gray-900">Warning: Week 5</h4>
                        <p class="text-sm text-gray-600 mt-1">
                            Week 5 (Machine Learning) is the "Heavy Hitter." It requires maximum cognitive load. Clear your calendar.
                        </p>
                    </div>
                </div>
                <div class="lg:col-span-2">
                    <div class="bg-white rounded-xl shadow-md p-6">
                        <div class="chart-container">
                            <canvas id="intensityChart"></canvas>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section 3: The 6-Week Roadmap (Timeline) -->
        <section>
            <div class="mb-12 text-center">
                <h2 class="text-3xl font-bold text-gray-900 mb-4">The 42-Day Roadmap</h2>
                <p class="text-gray-600 text-lg max-w-2xl mx-auto">
                    A day-by-day battle plan. Stick to this schedule to ensure you have a complete portfolio ready for recruiters by early March.
                </p>
            </div>

            <!-- Week 1 -->
            <div class="relative pl-12 pb-12 timeline-item">
                <div class="timeline-line"></div>
                <div class="absolute left-0 top-0 w-12 h-12 bg-blue-600 rounded-full flex items-center justify-center text-white font-bold text-xl shadow-lg z-10">1</div>
                <div class="bg-white rounded-lg shadow-md p-6 ml-4 hover:shadow-xl transition-shadow border-t-4 border-blue-600">
                    <div class="flex flex-col md:flex-row justify-between items-start md:items-center mb-4">
                        <h3 class="text-2xl font-bold text-gray-800">Foundations & Python Basics</h3>
                        <span class="bg-blue-100 text-blue-800 text-xs font-semibold px-3 py-1 rounded-full mt-2 md:mt-0">Days 1-7</span>
                    </div>
                    <p class="text-gray-600 mb-4">Master the PACE framework and get comfortable with Python syntax. This is your warm-up.</p>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
                        <div class="bg-gray-50 p-3 rounded">
                            <strong class="block text-gray-900 mb-1">Key Topics</strong>
                            <ul class="list-disc list-inside text-gray-600 space-y-1">
                                <li>Python Syntax & Variables</li>
                                <li>Control Flow (If/Else, Loops)</li>
                                <li>Data Structures (Lists, Dicts)</li>
                                <li>Intro to NumPy & Pandas</li>
                            </ul>
                        </div>
                        <div class="bg-yellow-50 p-3 rounded border border-yellow-200">
                            <strong class="block text-yellow-800 mb-1">Milestone</strong>
                            <p class="text-gray-700">Solve 5-10 HackerRank logic problems to solidify syntax.</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Week 2 -->
            <div class="relative pl-12 pb-12 timeline-item">
                <div class="timeline-line"></div>
                <div class="absolute left-0 top-0 w-12 h-12 bg-indigo-600 rounded-full flex items-center justify-center text-white font-bold text-xl shadow-lg z-10">2</div>
                <div class="bg-white rounded-lg shadow-md p-6 ml-4 hover:shadow-xl transition-shadow border-t-4 border-indigo-600">
                    <div class="flex flex-col md:flex-row justify-between items-start md:items-center mb-4">
                        <h3 class="text-2xl font-bold text-gray-800">EDA & Data Manipulation</h3>
                        <span class="bg-indigo-100 text-indigo-800 text-xs font-semibold px-3 py-1 rounded-full mt-2 md:mt-0">Days 8-14</span>
                    </div>
                    <p class="text-gray-600 mb-4">Dive into the data. Learn to clean messy datasets and visualize hidden patterns.</p>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
                        <div class="bg-gray-50 p-3 rounded">
                            <strong class="block text-gray-900 mb-1">Key Topics</strong>
                            <ul class="list-disc list-inside text-gray-600 space-y-1">
                                <li>Pandas DataFrames (Filter/Sort)</li>
                                <li>Matplotlib & Seaborn</li>
                                <li>Handling Missing Values</li>
                                <li>Detecting Outliers</li>
                            </ul>
                        </div>
                        <div class="bg-green-50 p-3 rounded border border-green-200">
                            <strong class="block text-green-800 mb-1">Portfolio Item</strong>
                            <p class="text-gray-700">Upload "TikTok/Waze" EDA project to GitHub.</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Week 3 -->
            <div class="relative pl-12 pb-12 timeline-item">
                <div class="timeline-line"></div>
                <div class="absolute left-0 top-0 w-12 h-12 bg-purple-600 rounded-full flex items-center justify-center text-white font-bold text-xl shadow-lg z-10">3</div>
                <div class="bg-white rounded-lg shadow-md p-6 ml-4 hover:shadow-xl transition-shadow border-t-4 border-purple-600">
                    <div class="flex flex-col md:flex-row justify-between items-start md:items-center mb-4">
                        <h3 class="text-2xl font-bold text-gray-800">Statistics for Data Science</h3>
                        <span class="bg-purple-100 text-purple-800 text-xs font-semibold px-3 py-1 rounded-full mt-2 md:mt-0">Days 15-21</span>
                    </div>
                    <p class="text-gray-600 mb-4">The math behind the magic. Crucial for technical interviews.</p>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
                        <div class="bg-gray-50 p-3 rounded">
                            <strong class="block text-gray-900 mb-1">Key Topics</strong>
                            <ul class="list-disc list-inside text-gray-600 space-y-1">
                                <li>Probability Distributions</li>
                                <li>Hypothesis Testing (P-values)</li>
                                <li>A/B Testing</li>
                                <li>Confidence Intervals</li>
                            </ul>
                        </div>
                        <div class="bg-yellow-50 p-3 rounded border border-yellow-200">
                            <strong class="block text-yellow-800 mb-1">Interview Prep</strong>
                            <p class="text-gray-700">Practice explaining "What is a P-value?" simply.</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Week 4 -->
            <div class="relative pl-12 pb-12 timeline-item">
                <div class="timeline-line"></div>
                <div class="absolute left-0 top-0 w-12 h-12 bg-pink-600 rounded-full flex items-center justify-center text-white font-bold text-xl shadow-lg z-10">4</div>
                <div class="bg-white rounded-lg shadow-md p-6 ml-4 hover:shadow-xl transition-shadow border-t-4 border-pink-600">
                    <div class="flex flex-col md:flex-row justify-between items-start md:items-center mb-4">
                        <h3 class="text-2xl font-bold text-gray-800">Regression Analysis</h3>
                        <span class="bg-pink-100 text-pink-800 text-xs font-semibold px-3 py-1 rounded-full mt-2 md:mt-0">Days 22-28</span>
                    </div>
                    <p class="text-gray-600 mb-4">Start predicting the future. Build models that define relationships between variables.</p>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
                        <div class="bg-gray-50 p-3 rounded">
                            <strong class="block text-gray-900 mb-1">Key Topics</strong>
                            <ul class="list-disc list-inside text-gray-600 space-y-1">
                                <li>Simple & Multiple Linear Regression</li>
                                <li>Logistic Regression (Classification)</li>
                                <li>Model Eval (RMSE, MAE)</li>
                                <li>Statsmodels library</li>
                            </ul>
                        </div>
                        <div class="bg-green-50 p-3 rounded border border-green-200">
                            <strong class="block text-green-800 mb-1">Resume Update</strong>
                            <p class="text-gray-700">Add "Statistical Modeling" to your skills section.</p>
                        </div>
                    </div>
                </div>
            </div>

             <!-- Week 5 -->
             <div class="relative pl-12 pb-12 timeline-item">
                <div class="timeline-line"></div>
                <div class="absolute left-0 top-0 w-12 h-12 bg-red-600 rounded-full flex items-center justify-center text-white font-bold text-xl shadow-lg z-10">5</div>
                <div class="bg-white rounded-lg shadow-md p-6 ml-4 hover:shadow-xl transition-shadow border-t-4 border-red-600 ring-2 ring-red-100">
                    <div class="flex flex-col md:flex-row justify-between items-start md:items-center mb-4">
                        <h3 class="text-2xl font-bold text-gray-800">Machine Learning (Heavy Hitter)</h3>
                        <span class="bg-red-100 text-red-800 text-xs font-semibold px-3 py-1 rounded-full mt-2 md:mt-0">Days 29-35</span>
                    </div>
                    <p class="text-gray-600 mb-4">The peak of the mountain. Advanced algorithms that set you apart.</p>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
                        <div class="bg-gray-50 p-3 rounded">
                            <strong class="block text-gray-900 mb-1">Key Topics</strong>
                            <ul class="list-disc list-inside text-gray-600 space-y-1">
                                <li>Decision Trees & Random Forests</li>
                                <li>Naive Bayes & KNN</li>
                                <li>Confusion Matrix, ROC-AUC</li>
                                <li>Hyperparameter Tuning</li>
                            </ul>
                        </div>
                        <div class="bg-yellow-50 p-3 rounded border border-yellow-200">
                            <strong class="block text-yellow-800 mb-1">Review</strong>
                            <p class="text-gray-700">Watch external videos (e.g., CodeWithHarry) on XGBoost/RF.</p>
                        </div>
                    </div>
                </div>
            </div>

            <!-- Week 6 -->
            <div class="relative pl-12 timeline-item">
                <!-- No line for last item -->
                <div class="absolute left-0 top-0 w-12 h-12 bg-green-600 rounded-full flex items-center justify-center text-white font-bold text-xl shadow-lg z-10">6</div>
                <div class="bg-white rounded-lg shadow-md p-6 ml-4 hover:shadow-xl transition-shadow border-t-4 border-green-600">
                    <div class="flex flex-col md:flex-row justify-between items-start md:items-center mb-4">
                        <h3 class="text-2xl font-bold text-gray-800">Capstone & Job Readiness</h3>
                        <span class="bg-green-100 text-green-800 text-xs font-semibold px-3 py-1 rounded-full mt-2 md:mt-0">Days 36-42</span>
                    </div>
                    <p class="text-gray-600 mb-4">The final stretch. Complete the Salifort Motors project and polish your profile.</p>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-4 text-sm">
                        <div class="bg-gray-50 p-3 rounded">
                            <strong class="block text-gray-900 mb-1">Key Topics</strong>
                            <ul class="list-disc list-inside text-gray-600 space-y-1">
                                <li>End-to-End Model Building</li>
                                <li>Executive Summary Writing</li>
                                <li>Mock Interviews</li>
                                <li>Final Submission</li>
                            </ul>
                        </div>
                        <div class="bg-green-50 p-3 rounded border border-green-200">
                            <strong class="block text-green-800 mb-1">Certification</strong>
                            <p class="text-gray-700">Download certificate and apply to "Early Career" roles.</p>
                        </div>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section 4: The Daily Strategy -->
        <section class="mb-16">
            <h2 class="text-3xl font-bold text-gray-900 mb-8 text-center">Optimization Strategy</h2>
            <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center bg-white rounded-xl shadow-lg p-8">
                <div>
                    <h3 class="text-2xl font-bold text-gray-800 mb-4">How to "Cheat" the Clock</h3>
                    <p class="text-gray-600 mb-4">To finish in 6 weeks, you cannot watch every second of every video. You must be strategic with your 4-5 daily hours.</p>
                    <ul class="space-y-4">
                        <li class="flex items-start">
                            <span class="text-2xl mr-3">📖</span>
                            <div>
                                <strong class="block text-gray-900">Read Transcripts</strong>
                                <span class="text-sm text-gray-500">Scan transcripts in 2 mins instead of watching 10 min videos. Only watch complex topics.</span>
                            </div>
                        </li>
                        <li class="flex items-start">
                            <span class="text-2xl mr-3">🧪</span>
                            <div>
                                <strong class="block text-gray-900">Prioritize Labs</strong>
                                <span class="text-sm text-gray-500">Hands-on coding is where 80% of learning happens. Spend the majority of your time here.</span>
                            </div>
                        </li>
                        <li class="flex items-start">
                            <span class="text-2xl mr-3">⚡</span>
                            <div>
                                <strong class="block text-gray-900">Batch Quizzes</strong>
                                <span class="text-sm text-gray-500">Don't wait for perfection. Take quizzes when 70% ready. You can always retake them.</span>
                            </div>
                        </li>
                    </ul>
                </div>
                <div>
                     <h3 class="text-xl font-bold text-gray-800 mb-2 text-center">Daily Time Allocation</h3>
                     <div class="chart-container">
                        <canvas id="dailyTimeChart"></canvas>
                    </div>
                </div>
            </div>
        </section>

        <!-- Footer -->
        <footer class="bg-gray-800 text-gray-300 py-8 text-center rounded-t-lg">
            <p class="mb-2">Generated for your March Placement Goal</p>
            <p class="text-sm text-gray-500">Based on Google Advanced Data Analytics Curriculum</p>
        </footer>

    </main>

    <script>
        // --- Gemini API Integration ---
        const apiKey = ""; // API Key provided at runtime

        async function callGemini(prompt, systemPrompt) {
            const loading = document.getElementById('loadingIndicator');
            loading.classList.remove('hidden');
            
            let retryCount = 0;
            const delays = [1000, 2000, 4000, 8000, 16000];

            const fetchContent = async () => {
                try {
                    const response = await fetch(`https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${apiKey}`, {
                        method: 'POST',
                        headers: { 'Content-Type': 'application/json' },
                        body: JSON.stringify({
                            contents: [{ parts: [{ text: prompt }] }],
                            systemInstruction: { parts: [{ text: systemPrompt }] }
                        })
                    });
                    
                    if (!response.ok) throw new Error('API Error');
                    const result = await response.json();
                    return result.candidates?.[0]?.content?.parts?.[0]?.text;
                } catch (error) {
                    if (retryCount < 5) {
                        await new Promise(r => setTimeout(r, delays[retryCount++]));
                        return fetchContent();
                    }
                    throw error;
                }
            };

            try {
                const text = await fetchContent();
                loading.classList.add('hidden');
                return text;
            } catch (err) {
                loading.classList.add('hidden');
                console.error(err);
                return "Sorry, I couldn't reach the AI right now. Please check your connection.";
            }
        }

        async function generateProject() {
            const interest = document.getElementById('interestInput').value || 'Any';
            const output = document.getElementById('projectOutput');
            output.classList.remove('hidden');
            output.innerText = "Generating project brief...";

            const systemPrompt = "You are a senior data science mentor. Suggest a unique, impressive data analytics capstone project brief based on the user's interest. Include: Project Title, Dataset suggestion, and 3 key analysis goals. Keep it under 100 words.";
            const userPrompt = `I am interested in ${interest}. Give me a Google Advanced Data Analytics level project idea.`;
            
            const result = await callGemini(userPrompt, systemPrompt);
            output.innerText = result;
        }

        async function explainConcept() {
            const concept = document.getElementById('conceptInput').value;
            const output = document.getElementById('conceptOutput');
            if (!concept) return;
            output.classList.remove('hidden');
            output.innerText = "Analyzing concept...";

            const systemPrompt = "Explain complex data science concepts in the simplest terms possible (EL5 style). Use a short analogy. Keep it under 60 words.";
            const userPrompt = `Explain the concept of: ${concept}`;
            
            const result = await callGemini(userPrompt, systemPrompt);
            output.innerText = result;
        }

        async function generateQuiz() {
            const topic = document.getElementById('topicSelect').value;
            const output = document.getElementById('quizOutput');
            output.classList.remove('hidden');
            output.innerText = "Preparing questions...";

            const systemPrompt = "Generate one tough multiple choice question for a data analyst interview about the selected topic. Include the answer and a brief explanation at the bottom.";
            const userPrompt = `Topic: ${topic}`;
            
            const result = await callGemini(userPrompt, systemPrompt);
            output.innerText = result;
        }

        // --- Chart Configurations (Existing) ---
        Chart.defaults.font.family = "'Roboto', sans-serif";
        Chart.defaults.color = '#4B5563';

        function formatLabel(str, maxwidth) {
            var sections = [];
            var words = str.split(" ");
            var temp = "";
            words.forEach(function(item, index) {
                if (temp.length > 0) {
                    var concat = temp + ' ' + item;
                    if (concat.length > maxwidth) {
                        sections.push(temp);
                        temp = "";
                    } else {
                        if (index == (words.length - 1)) {
                            sections.push(concat);
                            return;
                        } else {
                            temp = concat;
                            return;
                        }
                    }
                }
                if (index == (words.length - 1)) {
                    sections.push(item);
                    return;
                }
                if (item.length < maxwidth) {
                    temp = item;
                } else {
                    sections.push(item);
                }
            });
            return sections;
        }

        const standardTooltipConfig = {
            callbacks: {
                title: function(tooltipItems) {
                    const item = tooltipItems[0];
                    let label = item.chart.data.labels[item.dataIndex];
                    if (Array.isArray(label)) {
                        return label.join(' ');
                    } else {
                        return label;
                    }
                }
            }
        };

        const curriculumCtx = document.getElementById('curriculumChart').getContext('2d');
        const curriculumLabels = ['Foundations (Week 1)', 'Python Basics (Week 1)', 'EDA & Viz (Week 2)', 'Statistics (Week 3)', 'Regression (Week 4)', 'Machine Learning (Week 5)', 'Capstone (Week 6)'];
        const wrappedCurriculumLabels = curriculumLabels.map(l => formatLabel(l, 16));

        new Chart(curriculumCtx, {
            type: 'doughnut',
            data: {
                labels: wrappedCurriculumLabels,
                datasets: [{
                    label: 'Course Focus',
                    data: [10, 15, 15, 15, 15, 20, 10],
                    backgroundColor: ['#9CA3AF', '#60A5FA', '#3B82F6', '#8B5CF6', '#EC4899', '#EF4444', '#10B981'],
                    borderWidth: 0
                }]
            },
            options: {
                maintainAspectRatio: false,
                plugins: {
                    legend: { position: 'right' },
                    tooltip: standardTooltipConfig
                }
            }
        });

        const skillsCtx = document.getElementById('skillsRadarChart').getContext('2d');
        const skillLabels = ['Python Coding', 'Statistical Analysis', 'Machine Learning', 'Data Visualization', 'Business Comm', 'Data Cleaning'];
        const wrappedSkillLabels = skillLabels.map(l => formatLabel(l, 16));

        new Chart(skillsCtx, {
            type: 'radar',
            data: {
                labels: wrappedSkillLabels,
                datasets: [{
                    label: 'Starting Level',
                    data: [2, 3, 1, 3, 5, 2],
                    fill: true,
                    backgroundColor: 'rgba(156, 163, 175, 0.2)',
                    borderColor: 'rgb(156, 163, 175)',
                    pointBackgroundColor: 'rgb(156, 163, 175)',
                    pointBorderColor: '#fff'
                }, {
                    label: 'Post-Sprint Level',
                    data: [8, 8, 7, 9, 8, 9],
                    fill: true,
                    backgroundColor: 'rgba(59, 130, 246, 0.2)',
                    borderColor: 'rgb(59, 130, 246)',
                    pointBackgroundColor: 'rgb(59, 130, 246)',
                    pointBorderColor: '#fff'
                }]
            },
            options: {
                maintainAspectRatio: false,
                scales: { r: { suggestedMin: 0, suggestedMax: 10 } },
                plugins: { tooltip: standardTooltipConfig }
            }
        });

        const intensityCtx = document.getElementById('intensityChart').getContext('2d');
        new Chart(intensityCtx, {
            type: 'bar',
            data: {
                labels: ['Week 1', 'Week 2', 'Week 3', 'Week 4', 'Week 5', 'Week 6'],
                datasets: [{
                    label: 'Cognitive Load (1-10)',
                    data: [5, 6, 7, 8, 10, 7],
                    backgroundColor: ['#60A5FA', '#60A5FA', '#8B5CF6', '#EC4899', '#EF4444', '#10B981'],
                    borderRadius: 6
                }]
            },
            options: {
                maintainAspectRatio: false,
                scales: { y: { beginAtZero: true, max: 10 } },
                plugins: { legend: { display: false }, tooltip: standardTooltipConfig }
            }
        });

        const dailyCtx = document.getElementById('dailyTimeChart').getContext('2d');
        const dailyLabels = ['Hands-on Labs (Coding)', 'Video Lectures (Concepts)', 'Project Work (Portfolio)', 'Review & Quizzes'];
        const wrappedDailyLabels = dailyLabels.map(l => formatLabel(l, 16));

        new Chart(dailyCtx, {
            type: 'pie',
            data: {
                labels: wrappedDailyLabels,
                datasets: [{
                    label: 'Hours Allocation',
                    data: [40, 20, 30, 10],
                    backgroundColor: ['#3B82F6', '#9CA3AF', '#F59E0B', '#10B981'],
                    hoverOffset: 4
                }]
            },
            options: {
                maintainAspectRatio: false,
                plugins: { legend: { position: 'bottom' }, tooltip: standardTooltipConfig }
            }
        });

    </script>
</body>
</html>
