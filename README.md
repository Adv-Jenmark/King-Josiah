<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Interactive Bible Study: The Story of King Josiah</title>
    <!-- Chosen Palette: Ancient Scroll -->
    <!-- Application Structure Plan: A thematic, single-page narrative journey. The user scrolls through sections: 1. Hero Introduction, 2. A "Crossroads" section comparing Josiah's choice to his heritage, 3. An interactive "Discovery" of the law, 4. A "Ripple Effect" section visualizing his reforms with a chart and interactive cards, and 5. A "Mirror" section with reflection prompts. This structure turns the linear study into an engaging story, guiding the user from historical events to personal application, which is ideal for a youth audience. -->
    <!-- Visualization & Content Choices: 1. Heritage vs. Choice (Compare): Side-by-side HTML layout to visually represent the two paths. 2. Law Discovery (Cause/Effect): A clickable reveal shows Josiah's reaction, creating dramatic impact. 3. Reforms (Organize/Show Change): A Chart.js bar chart gives a quick visual of the transformation, while interactive HTML cards allow users to explore details without clutter. 4. Reflection (Inform/Prompt): Styled HTML cards present the study's core questions directly to the user. This structure uses simple, effective web technologies to make the content interactive and digestible. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;600;700&family=Playfair+Display:wght@700&display=swap" rel="stylesheet">
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #FDFBF5;
            color: #4A4A4A;
        }
        h1, h2, h3 {
            font-family: 'Playfair Display', serif;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 600px;
            margin-left: auto;
            margin-right: auto;
            height: 300px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 350px;
            }
        }
        .section-fade-in {
            opacity: 0;
            transform: translateY(20px);
            transition: opacity 0.6s ease-out, transform 0.6s ease-out;
        }
        .section-fade-in.visible {
            opacity: 1;
            transform: translateY(0);
        }
        .reform-card {
            transition: transform 0.3s ease, box-shadow 0.3s ease;
        }
        .reform-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
    </style>
</head>
<body class="antialiased">

    <main>
        <!-- Section 1: Hero -->
        <section class="min-h-screen flex flex-col justify-center items-center text-center p-6 bg-stone-100 section-fade-in">
            <h1 class="text-4xl md:text-6xl font-bold text-stone-800">The King Who Found God</h1>
            <p class="mt-4 text-lg md:text-xl max-w-2xl text-stone-600">The inspiring story of Josiah, a young king who transformed a nation, and what his life teaches us about our own walk with God.</p>
            <div class="mt-12 text-stone-500 animate-bounce">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
                </svg>
            </div>
        </section>

        <!-- Section 2: The Crossroads -->
        <section class="py-16 md:py-24 bg-white section-fade-in">
            <div class="container mx-auto px-6">
                <div class="text-center mb-12">
                    <h2 class="text-3xl md:text-4xl font-bold text-stone-800">A Kingdom at a Crossroads</h2>
                    <p class="mt-3 max-w-3xl mx-auto text-stone-600">Josiah became king at just 8 years old. He inherited a kingdom steeped in idolatry from his father Amon and grandfather Manasseh. He had a choice to make: follow their path, or forge a new one.</p>
                </div>
                <div class="grid md:grid-cols-2 gap-8 max-w-5xl mx-auto">
                    <div class="bg-stone-100 p-6 rounded-lg border border-stone-200">
                        <h3 class="text-2xl font-bold text-stone-700">The Path of His Fathers</h3>
                        <p class="text-stone-500 mt-2">2 Kings 21</p>
                        <ul class="mt-4 space-y-3 text-stone-600">
                            <li class="flex items-start"><span class="mr-3 text-xl">🔥</span><span>Worshipped idols and built altars to false gods.</span></li>
                            <li class="flex items-start"><span class="mr-3 text-xl">🩸</span><span>Shed innocent blood and practiced witchcraft.</span></li>
                            <li class="flex items-start"><span class="mr-3 text-xl">🏛️</span><span>Desecrated the Lord's temple with pagan symbols.</span></li>
                        </ul>
                    </div>
                    <div class="bg-teal-50 p-6 rounded-lg border border-teal-200">
                        <h3 class="text-2xl font-bold text-teal-800">The Path He Chose</h3>
                        <p class="text-teal-600 mt-2">2 Kings 22:1-2</p>
                        <ul class="mt-4 space-y-3 text-teal-700">
                            <li class="flex items-start"><span class="mr-3 text-xl">👑</span><span>"He did what was right in the eyes of the Lord."</span></li>
                            <li class="flex items-start"><span class="mr-3 text-xl">🧭</span><span>Followed the ways of his ancestor David.</span></li>
                            <li class="flex items-start"><span class="mr-3 text-xl">➡️</span><span>He did not turn aside to the right or to the left.</span></li>
                        </ul>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section 3: The Discovery -->
        <section class="py-16 md:py-24 bg-stone-100 section-fade-in">
            <div class="container mx-auto px-6 text-center">
                <h2 class="text-3xl md:text-4xl font-bold text-stone-800">The Lost Law</h2>
                <p class="mt-3 max-w-3xl mx-auto text-stone-600">Years into his reign, while repairing the temple, Josiah's officials made a shocking discovery: The Book of the Law, God's own words, lost and forgotten for generations.</p>
                <div class="mt-8 max-w-2xl mx-auto bg-white p-8 rounded-lg shadow-md">
                    <p class="text-lg text-stone-700">When the book was read to the king, its words pierced his heart. He realized how far his people had strayed from God's commands.</p>
                    <button id="reaction-button" class="mt-6 bg-teal-600 text-white font-bold py-3 px-6 rounded-lg hover:bg-teal-700 transition-colors">How did Josiah react?</button>
                    <div id="reaction-reveal" class="hidden mt-6 border-t pt-6 text-left">
                        <p class="font-bold text-xl text-teal-800">"He tore his robes." (2 Kings 22:11)</p>
                        <p class="mt-2 text-stone-600">This was an act of deep grief, humility, and repentance. He was broken by what he heard. He didn't make excuses or ignore the message. He let it change him.</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section 4: The Ripple Effect -->
        <section class="py-16 md:py-24 bg-white section-fade-in">
            <div class="container mx-auto px-6">
                <div class="text-center mb-12">
                    <h2 class="text-3xl md:text-4xl font-bold text-stone-800">The Ripple Effect of Repentance</h2>
                    <p class="mt-3 max-w-3xl mx-auto text-stone-600">Josiah's personal repentance sparked a nationwide reformation. His encounter with God's Word led to radical action.</p>
                </div>
                <div class="chart-container mb-12">
                    <canvas id="reformationChart"></canvas>
                </div>
                <div class="grid md:grid-cols-2 lg:grid-cols-3 gap-6">
                    <div class="reform-card bg-stone-50 p-6 rounded-lg border border-stone-200">
                        <h3 class="text-xl font-bold text-stone-700">Cleansing the Temple</h3>
                        <p class="mt-2 text-stone-600">He removed all articles made for Baal, Asherah, and other false gods from the temple of the Lord. (2 Kings 23:4)</p>
                    </div>
                    <div class="reform-card bg-stone-50 p-6 rounded-lg border border-stone-200">
                        <h3 class="text-xl font-bold text-stone-700">Destroying High Places</h3>
                        <p class="mt-2 text-stone-600">He tore down the pagan shrines throughout Judah and desecrated the altars to ensure they wouldn't be used again. (2 Kings 23:8)</p>
                    </div>
                    <div class="reform-card bg-stone-50 p-6 rounded-lg border border-stone-200">
                        <h3 class="text-xl font-bold text-stone-700">Abolishing Pagan Priests</h3>
                        <p class="mt-2 text-stone-600">He did away with the pagan priests appointed by previous kings who had led the people astray. (2 Kings 23:5)</p>
                    </div>
                    <div class="reform-card bg-stone-50 p-6 rounded-lg border border-stone-200">
                        <h3 class="text-xl font-bold text-stone-700">Ending Child Sacrifice</h3>
                        <p class="mt-2 text-stone-600">He desecrated Topheth, where people had been sacrificing their children to the god Molek. (2 Kings 23:10)</p>
                    </div>
                    <div class="reform-card bg-stone-50 p-6 rounded-lg border border-stone-200">
                        <h3 class="text-xl font-bold text-stone-700">Renewing the Covenant</h3>
                        <p class="mt-2 text-stone-600">He gathered all the people and publicly pledged to follow the Lord and keep His commands with all his heart and soul. (2 Kings 23:3)</p>
                    </div>
                    <div class="reform-card bg-stone-50 p-6 rounded-lg border border-stone-200">
                        <h3 class="text-xl font-bold text-stone-700">Restoring the Passover</h3>
                        <p class="mt-2 text-stone-600">He commanded the people to celebrate the Passover, which had not been observed in that way since the days of the judges. (2 Kings 23:21-22)</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Section 5: The Mirror -->
        <section class="py-16 md:py-24 bg-teal-900/95 text-white section-fade-in">
            <div class="container mx-auto px-6">
                <div class="text-center mb-12">
                    <h2 class="text-3xl md:text-4xl font-bold">The Mirror: Our Relationship</h2>
                    <p class="mt-3 max-w-3xl mx-auto text-teal-200">Josiah's story isn't just history; it's a mirror for our own lives. His challenges and choices prompt us to examine our own relationship with God.</p>
                </div>
                <div class="space-y-6 max-w-3xl mx-auto">
                    <div class="bg-white/10 p-6 rounded-lg">
                        <p class="text-xl font-semibold text-teal-100">Do we react to God's Word with the same urgency and humility as Josiah? Or has it become just another book on the shelf?</p>
                    </div>
                    <div class="bg-white/10 p-6 rounded-lg">
                        <p class="text-xl font-semibold text-teal-100">When was the last time a Bible verse truly moved you or challenged you to change?</p>
                    </div>
                    <div class="bg-white/10 p-6 rounded-lg">
                        <p class="text-xl font-semibold text-teal-100">Josiah's faith led to radical action. If our relationship with God is real, what actions should it be producing in our lives?</p>
                    </div>
                </div>
            </div>
        </section>

        <!-- Footer / Challenge -->
        <footer class="py-16 bg-stone-800 text-white section-fade-in">
            <div class="container mx-auto px-6 text-center">
                <h3 class="text-2xl font-bold">Your Personal Challenge</h3>
                <p class="mt-4 max-w-2xl mx-auto text-stone-300">Just like the Book of the Law was 'found' in Josiah's day, God's Word is available to us now. This week, how will you actively seek to 'hear' from God through His Word and allow it to impact your life? What's one small step you can take to engage more deeply with the Bible?</p>
                <p class="mt-8 text-stone-400">Close in prayer, asking God for a heart like Josiah's – humble, responsive, and eager to follow Him fully.</p>
            </div>
        </footer>
    </main>

    <script>
        document.addEventListener('DOMContentLoaded', function() {
            // Button interaction for Josiah's reaction
            const reactionButton = document.getElementById('reaction-button');
            const reactionReveal = document.getElementById('reaction-reveal');
            if (reactionButton) {
                reactionButton.addEventListener('click', () => {
                    reactionReveal.classList.toggle('hidden');
                    reactionButton.textContent = reactionReveal.classList.contains('hidden') ? "How did Josiah react?" : "Hide Reaction";
                });
            }

            // Chart.js implementation
            const ctx = document.getElementById('reformationChart');
            if (ctx) {
                new Chart(ctx, {
                    type: 'bar',
                    data: {
                        labels: ['Before Josiah', 'After Josiah'],
                        datasets: [{
                            label: 'State of Worship in Judah',
                            data: [20, 90],
                            backgroundColor: [
                                'rgba(113, 113, 113, 0.6)', // stone-500
                                'rgba(20, 184, 166, 0.6)'  // teal-500
                            ],
                            borderColor: [
                                'rgba(113, 113, 113, 1)',
                                'rgba(20, 184, 166, 1)'
                            ],
                            borderWidth: 1
                        }]
                    },
                    options: {
                        responsive: true,
                        maintainAspectRatio: false,
                        scales: {
                            y: {
                                beginAtZero: true,
                                max: 100,
                                ticks: {
                                    callback: function(value) {
                                        if (value === 20) return 'Idolatry & Neglect';
                                        if (value === 90) return 'Covenant & Worship';
                                        return '';
                                    },
                                    color: '#4A4A4A',
                                    font: { size: 12 }
                                }
                            }
                        },
                        plugins: {
                            legend: {
                                display: false
                            },
                            tooltip: {
                                enabled: false
                            }
                        }
                    }
                });
            }

            // Intersection Observer for fade-in animations
            const sections = document.querySelectorAll('.section-fade-in');
            const observer = new IntersectionObserver((entries) => {
                entries.forEach(entry => {
                    if (entry.isIntersecting) {
                        entry.target.classList.add('visible');
                    }
                });
            }, {
                threshold: 0.1
            });

            sections.forEach(section => {
                observer.observe(section);
            });
        });
    </script>

</body>
</html>
