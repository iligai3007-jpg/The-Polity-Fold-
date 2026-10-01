# The-Polity-Fold-
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>The Polity Fold | Student Political & Legal Publication</title>
  
  <!-- Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@500;700&family=Newsreader:ital,opsz,wght@0,6..72,400;0,6..72,600;1,6..72,400&family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
  
  <!-- Tailwind CSS CDN -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            navy: {
              DEFAULT: '#0B1325',
              light: '#14213D',
              deep: '#050914'
            },
            cream: {
              DEFAULT: '#FDFBF7',
              muted: '#F4EFE6',
              dark: '#EAE1D0'
            },
            accent: {
              highlight: 'rgba(234, 179, 8, 0.35)',
              border: '#D4AF37'
            }
          },
          fontFamily: {
            serif: ['Newsreader', 'Georgia', 'serif'],
            display: ['Cinzel', 'serif'],
            sans: ['Plus Jakarta Sans', 'sans-serif']
          }
        }
      }
    }
  </script>
  <style>
    ::selection {
      background: rgba(234, 179, 8, 0.4);
      color: #0B1325;
    }
    .annotated-highlight {
      background-color: rgba(234, 179, 8, 0.35);
      border-bottom: 2px solid #D4AF37;
      cursor: pointer;
      position: relative;
    }
    .annotated-highlight:hover {
      background-color: rgba(234, 179, 8, 0.55);
    }
  </style>
</head>
<body class="bg-cream text-navy font-sans antialiased min-h-screen flex flex-col">

  <!-- TOP BAR -->
  <header class="bg-navy text-cream border-b border-cream/10 sticky top-0 z-40">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <div class="flex items-center justify-between h-16">
        
        <!-- Brand / Logo -->
        <div class="flex items-center space-x-3 cursor-pointer" onclick="navigate('home')">
          <svg class="w-8 h-8 text-cream fill-current" viewBox="0 0 24 24">
            <path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/>
          </svg>
          <span class="font-display font-bold text-xl tracking-wider text-cream">THE POLITY FOLD</span>
        </div>

        <!-- Navigation Links -->
        <nav class="hidden md:flex items-center space-x-8 text-sm font-medium tracking-wide">
          <button onclick="navigate('op-eds')" class="hover:text-amber-400 transition">Op-Eds</button>
          <button onclick="navigate('law-made-easy')" class="hover:text-amber-400 transition">Law Made Easy</button>
          <button onclick="navigate('contributors')" class="hover:text-amber-400 transition">Contributors</button>
          <button onclick="navigate('about')" class="hover:text-amber-400 transition">About</button>
          <button onclick="navigate('pigeon')" class="text-amber-300 hover:text-amber-200 transition">Become a Polity Pigeon</button>
        </nav>

        <!-- User Controls -->
        <div id="user-controls" class="flex items-center space-x-4">
          <!-- Rendered via JS -->
        </div>
      </div>
    </div>
  </header>

  <!-- SELECTION TOOLBAR FOR ANNOTATIONS -->
  <div id="annotation-toolbar" class="hidden fixed z-50 bg-navy text-cream px-3 py-1.5 rounded shadow-lg flex items-center space-x-2 text-xs border border-cream/20">
    <button onclick="createAnnotation()" class="hover:text-amber-400 font-semibold flex items-center gap-1">
      ✏️ Add Note
    </button>
  </div>

  <!-- MAIN CONTENT CONTAINER -->
  <main id="app" class="flex-grow max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-8">
    <!-- Dynamic View Injected Here -->
  </main>

  <!-- FOOTER -->
  <footer class="bg-navy border-t border-cream/10 text-cream/70 py-12 mt-16">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 grid grid-cols-1 md:grid-cols-4 gap-8">
      <div>
        <h3 class="font-display font-bold text-cream text-lg mb-3">THE POLITY FOLD</h3>
        <p class="text-sm leading-relaxed">A student-led political and legal publication and educational platform for young people.</p>
      </div>
      <div>
        <h4 class="font-semibold text-cream text-sm mb-3">Sections</h4>
        <ul class="space-y-2 text-sm">
          <li><a href="#" onclick="navigate('op-eds')" class="hover:underline">Op-Eds & Analysis</a></li>
          <li><a href="#" onclick="navigate('law-made-easy')" class="hover:underline">Law Made Easy</a></li>
          <li><a href="#" onclick="navigate('contributors')" class="hover:underline">Contributors</a></li>
        </ul>
      </div>
      <div>
        <h4 class="font-semibold text-cream text-sm mb-3">Community</h4>
        <ul class="space-y-2 text-sm">
          <li><a href="#" onclick="navigate('pigeon')" class="hover:underline">Become a Polity Pigeon</a></li>
          <li><a href="#" onclick="navigate('about')" class="hover:underline">Write for The Polity Fold</a></li>
        </ul>
      </div>
      <div>
        <h4 class="font-semibold text-cream text-sm mb-3">Account</h4>
        <div id="footer-account-links" class="space-y-2 text-sm flex flex-col">
          <!-- Rendered via JS -->
        </div>
      </div>
    </div>
  </footer>

  <!-- SCRIPT / APPLICATION LOGIC -->
  <script>
    // --- STATE MANAGEMENT ---
    const state = {
      currentUser: JSON.parse(localStorage.getItem('pf_user')) || null, // { name, email, role: 'user'|'admin' }
      currentView: 'home',
      currentArticleId: null,
      currentLessonId: null,
      annotations: JSON.parse(localStorage.getItem('pf_annotations')) || [],
      progress: JSON.parse(localStorage.getItem('pf_progress')) || [],
      articles: [
        {
          id: 'op1',
          title: 'The Re-Emergence of Stare Decisis in Modern Constitutional Debates',
          subtitle: 'Why judicial precedent remains the bedrock of legal stability in unstable times.',
          author: 'Alexander Vance',
          category: 'Law',
          date: 'Oct 24, 2026',
          readTime: '6 min read',
          content: `The principle of *stare decisis*—Latin for "to stand by things decided"—is far more than an academic concept. It is the structural anchor of democratic rule of law. When courts adhere to settled legal precedent, they ensure that the law develops with continuity rather than shifting unpredictably with judicial appointments. In evaluating recent decisions, legal scholars have questioned whether historical precedents are receiving adequate deference or being discarded too readily.`,
        },
        {
          id: 'op2',
          title: 'Digital Sovereignty: How Tech Policy Re-Shapes Foreign Relations',
          subtitle: 'National borders are extending into cloud infrastructure and data centers.',
          author: 'Maya Lin',
          category: 'International Affairs',
          date: 'Oct 20, 2026',
          readTime: '5 min read',
          content: `Across global capitals, cyber jurisdiction has replaced physical territory as the new frontier of sovereignty. When national governments dictate where user data must reside, they are redefining public international law.`,
        }
      ],
      lessons: [
        {
          id: 'les1',
          course: 'Constitutional Law',
          title: 'Understanding Judicial Review',
          number: 101,
          difficulty: 'Beginner',
          description: 'Learn how courts evaluate whether executive actions or laws violate the Constitution.',
          content: `Judicial review allows courts to inspect acts of the legislative and executive branches. Established famously in *Marbury v. Madison*, this mechanism ensures the fundamental law of the constitution remains supreme over conflicting statutory statutes.`
        }
      ]
    };

    // --- NAVIGATION LOGIC ---
    function navigate(view, params = {}) {
      state.currentView = view;
      if (params.articleId) state.currentArticleId = params.articleId;
      if (params.lessonId) state.currentLessonId = params.lessonId;
      render();
      window.scrollTo(0, 0);
    }

    // --- AUTH LOGIC ---
    function login(role = 'user') {
      const name = role === 'admin' ? 'Editor-in-Chief' : 'Student Reader';
      const email = role === 'admin' ? 'admin@polityfold.org' : 'student@polityfold.org';
      state.currentUser = { name, email, role };
      localStorage.setItem('pf_user', JSON.stringify(state.currentUser));
      render();
    }

    function logout() {
      state.currentUser = null;
      localStorage.removeItem('pf_user');
      render();
    }

    // --- ANNOTATION ENGINE ---
    let activeSelectionRange = null;

    document.addEventListener('selectionchange', () => {
      const selection = window.getSelection();
      const toolbar = document.getElementById('annotation-toolbar');
      
      if (!state.currentUser) return;
      if (selection.isCollapsed || !selection.toString().trim()) {
        toolbar.classList.add('hidden');
        return;
      }

      const container = document.getElementById('selectable-content');
      if (container && container.contains(selection.anchorNode)) {
        const range = selection.getRangeAt(0);
        const rect = range.getBoundingClientRect();
        activeSelectionRange = range;
        
        toolbar.style.top = `${rect.top + window.scrollY - 35}px`;
        toolbar.style.left = `${rect.left + window.scrollX}px`;
        toolbar.classList.remove('hidden');
      } else {
        toolbar.classList.add('hidden');
      }
    });

    function createAnnotation() {
      if (!activeSelectionRange || !state.currentUser) return;
      const text = activeSelectionRange.toString();
      const note = prompt(`Add a private note for:\n"${text.substring(0, 40)}..."`);
      
      if (note !== null) {
        const annotation = {
          id: Date.now(),
          userEmail: state.currentUser.email,
          contentId: state.currentArticleId || state.currentLessonId,
          contentType: state.currentArticleId ? 'article' : 'lesson',
          text: text,
          note: note,
          date: new Date().toLocaleDateString()
        };
        
        state.annotations.push(annotation);
        localStorage.setItem('pf_annotations', JSON.stringify(state.annotations));
        document.getElementById('annotation-toolbar').classList.add('hidden');
        window.getSelection().removeAllRanges();
        render();
      }
    }

    // --- UI RENDERING ENGINE ---
    function render() {
      renderUserControls();
      const app = document.getElementById('app');

      switch (state.currentView) {
        case 'home':
          app.innerHTML = renderHome();
          break;
        case 'op-eds':
          app.innerHTML = renderOpEds();
          break;
        case 'article':
          app.innerHTML = renderArticle();
          break;
        case 'law-made-easy':
          app.innerHTML = renderLawMadeEasy();
          break;
        case 'lesson':
          app.innerHTML = renderLesson();
          break;
        case 'dashboard':
          app.innerHTML = renderDashboard();
          break;
        case 'admin':
          app.innerHTML = renderAdmin();
          break;
        case 'pigeon':
          app.innerHTML = renderPigeon();
          break;
        default:
          app.innerHTML = `<p class="py-12 text-center text-gray-600">Page under construction.</p>`;
      }
    }

    function renderUserControls() {
      const container = document.getElementById('user-controls');
      const footerContainer = document.getElementById('footer-account-links');

      if (state.currentUser) {
        container.innerHTML = `
          <button onclick="navigate('dashboard')" class="text-sm font-semibold hover:text-amber-400 transition">${state.currentUser.name}</button>
          ${state.currentUser.role === 'admin' ? '<button onclick="navigate(\'admin\')" class="text-xs bg-amber-500 text-navy px-2.5 py-1 rounded font-bold">ADMIN</button>' : ''}
          <button onclick="logout()" class="text-xs text-cream/70 hover:text-cream">Sign Out</button>
        `;
        footerContainer.innerHTML = `
          <button onclick="navigate('dashboard')" class="text-left hover:underline">My Dashboard & Annotations</button>
          <button onclick="logout()" class="text-left hover:underline">Sign Out</button>
        `;
      } else {
        container.innerHTML = `
          <button onclick="login('user')" class="text-sm hover:text-amber-400 transition">Sign In (Student)</button>
          <button onclick="login('admin')" class="text-xs bg-cream/10 border border-cream/30 hover:bg-cream/20 px-3 py-1.5 rounded transition">Admin Demo</button>
        `;
        footerContainer.innerHTML = `
          <button onclick="login('user')" class="text-left hover:underline">Student Sign In</button>
        `;
      }
    }

    // --- PAGE VIEWS ---
    function renderHome() {
      const feat = state.articles[0];
      return `
        <!-- HERO HEADLINE -->
        <div class="border-b border-navy/10 pb-8 mb-12 text-center">
          <p class="font-display text-xs tracking-widest text-navy/60 mb-2 uppercase">The Student Journal of Law & Policy</p>
          <h1 class="font-serif text-5xl md:text-6xl font-bold tracking-tight text-navy mb-4">THE POLITY FOLD</h1>
          <p class="text-lg text-navy/70 max-w-2xl mx-auto font-serif italic">Fostering critical legal reasoning and political debate for the next generation of civic leaders.</p>
        </div>

        <!-- FEATURED ARTICLE -->
        <section class="mb-16">
          <div class="grid md:grid-cols-12 gap-8 items-center bg-cream-muted p-8 rounded border border-navy/10">
            <div class="md:col-span-7">
              <span class="text-xs font-bold text-amber-700 uppercase tracking-widest">${feat.category}</span>
              <h2 class="font-serif text-3xl font-bold mt-2 mb-3 cursor-pointer hover:text-amber-800" onclick="navigate('article', {articleId: '${feat.id}'})">${feat.title}</h2>
              <p class="text-navy/80 font-serif mb-4 leading-relaxed">${feat.subtitle}</p>
              <div class="text-xs text-navy/60 flex items-center gap-4 font-sans">
                <span>By ${feat.author}</span>
                <span>•</span>
                <span>${feat.date}</span>
                <span>•</span>
                <span>${feat.readTime}</span>
              </div>
            </div>
            <div class="md:col-span-5 bg-navy text-cream p-6 rounded text-center">
              <p class="font-display text-lg mb-2">Law Made Easy</p>
              <p class="text-xs text-cream/70 mb-4">Learn to think like a lawyer with our structured interactive modules.</p>
              <button onclick="navigate('law-made-easy')" class="w-full bg-amber-400 text-navy font-bold py-2 px-4 rounded text-xs tracking-wider uppercase hover:bg-amber-300 transition">Explore Courses</button>
            </div>
          </div>
        </section>

        <!-- LATEST OP-EDS GRID -->
        <section class="mb-12">
          <h3 class="font-display text-lg font-bold border-b-2 border-navy mb-6 pb-1">Latest Commentary</h3>
          <div class="grid md:grid-cols-2 gap-8">
            ${state.articles.map(art => `
              <div class="border-b border-navy/10 pb-6">
                <span class="text-xs font-bold text-amber-800 uppercase tracking-wider">${art.category}</span>
                <h4 class="font-serif text-2xl font-bold mt-1 mb-2 cursor-pointer hover:text-amber-800" onclick="navigate('article', {articleId: '${art.id}'})">${art.title}</h4>
                <p class="text-navy/70 text-sm font-serif mb-3">${art.subtitle}</p>
                <div class="text-xs text-navy/50 font-sans">${art.author} \vert{}${art.date}</div>
              </div>
            `).join('')}
          </div>
        </section>
      `;
    }

    function renderOpEds() {
      return `
        <div class="border-b border-navy/10 pb-4 mb-8">
          <h1 class="font-serif text-4xl font-bold">Op-Eds & Analysis</h1>
          <p class="text-navy/70 font-serif italic mt-1">Student perspectives on pressing legal and political issues.</p>
        </div>
        <div class="space-y-8">
          ${state.articles.map(art => `
            <div class="bg-white p-6 rounded border border-navy/10 shadow-sm cursor-pointer hover:border-navy/30 transition" onclick="navigate('article', {articleId: '${art.id}'})">
              <span class="text-xs font-bold text-amber-800 uppercase">${art.category}</span>
              <h2 class="font-serif text-2xl font-bold mt-1 mb-2">${art.title}</h2>
              <p class="text-navy/70 font-serif mb-4">${art.subtitle}</p>
              <div class="text-xs text-navy/50">${art.author} • ${art.date} •${art.readTime}</div>
            </div>
          `).join('')}
        </div>
      `;
    }

    function renderArticle() {
      const art = state.articles.find(a => a.id === state.currentArticleId) || state.articles[0];
      const userAnnots = state.annotations.filter(a => a.contentId === art.id && (!state.currentUser || a.userEmail === state.currentUser.email));

      return `
        <article class="max-w-3xl mx-auto">
          <div class="mb-8 border-b border-navy/10 pb-6">
            <span class="text-xs font-bold text-amber-800 uppercase tracking-widest">${art.category}</span>
            <h1 class="font-serif text-4xl font-bold mt-2 mb-3 text-navy">${art.title}</h1>
            <p class="text-xl text-navy/70 font-serif italic mb-4">${art.subtitle}</p>
            <div class="text-xs text-navy/60 flex items-center justify-between">
              <span>By <strong>${art.author}</strong> | ${art.date}</span>
              <span>${art.readTime}</span>
            </div>
          </div>

          ${state.currentUser ? `
            <div class="bg-amber-50 border-l-4 border-amber-400 p-3 mb-6 text-xs text-amber-900">
              💡 <strong>Tip:</strong> Highlight any text below to add private personal study notes!
            </div>
          ` : ''}

          <!-- ARTICLE BODY WITH HIGHLIGHTABLE CONTENT -->
          <div id="selectable-content" class="font-serif text-lg leading-relaxed text-navy space-y-6">
            <p>${art.content}</p>
          </div>

          <!-- USER NOTES SECTION -->
          <div class="mt-12 pt-8 border-t border-navy/20">
            <h3 class="font-display font-bold text-lg mb-4">Your Private Annotations (${userAnnots.length})</h3>
            ${userAnnots.length === 0 ? `<p class="text-xs text-navy/50 italic">No notes created yet for this article.</p>` : `
              <div class="space-y-3">
                ${userAnnots.map(a => `
                  <div class="bg-cream-muted p-3 rounded text-xs border border-navy/10">
                    <p class="font-semibold text-amber-900 border-l-2 border-amber-500 pl-2 mb-1">"${a.text}"</p>
                    <p class="text-navy/80 font-sans">${a.note}</p>
                  </div>
                `).join('')}
              </div>
            `}
          </div>
        </article>
      `;
    }

    function renderLawMadeEasy() {
      return `
        <div class="border-b border-navy/10 pb-4 mb-8">
          <h1 class="font-serif text-4xl font-bold">Law Made Easy</h1>
          <p class="text-navy/70 font-serif italic mt-1">Law school concepts simplified for secondary students.</p>
        </div>
        <div class="grid md:grid-cols-2 gap-6">
          ${state.lessons.map(les => `
            <div class="bg-white p-6 rounded border border-navy/10 shadow-sm">
              <span class="text-xs font-bold bg-navy text-cream px-2 py-0.5 rounded">${les.course}</span>
              <h2 class="font-serif text-xl font-bold mt-3 mb-2">${les.title}</h2>
              <p class="text-sm text-navy/70 mb-4">${les.description}</p>
              <button onclick="navigate('lesson', {lessonId: '${les.id}'})" class="bg-navy text-cream text-xs px-4 py-2 rounded font-semibold hover:bg-navy-light transition">Start Lesson →</button>
            </div>
          `).join('')}
        </div>
      `;
    }

    function renderLesson() {
      const les = state.lessons.find(l => l.id === state.currentLessonId) || state.lessons[0];
      return `
        <div class="max-w-3xl mx-auto">
          <span class="text-xs font-bold text-amber-800 uppercase tracking-widest">${les.course}</span>
          <h1 class="font-serif text-3xl font-bold mt-1 mb-4">${les.title}</h1>
          
          <div id="selectable-content" class="bg-white p-8 rounded border border-navy/10 font-serif text-lg leading-relaxed space-y-4 mb-6">
            <p>${les.content}</p>
          </div>

          <div class="bg-cream-muted p-6 rounded border border-navy/10">
            <h3 class="font-display font-bold text-sm uppercase tracking-wider mb-2">Legal Reasoning Challenge</h3>
            <p class="text-sm font-serif mb-4">Based on this concept, how would you evaluate a case where a statute contradicts a constitutionally guaranteed right?</p>
            <textarea placeholder="Draft your rationale here..." class="w-full text-xs p-3 rounded border border-navy/20 font-sans"></textarea>
          </div>
        </div>
      `;
    }

    function renderDashboard() {
      if (!state.currentUser) return `<p class="text-center py-12">Please sign in to view your dashboard.</p>`;
      const userAnnots = state.annotations.filter(a => a.userEmail === state.currentUser.email);

      return `
        <div class="max-w-4xl mx-auto">
          <h1 class="font-serif text-3xl font-bold mb-2">Student Study Dashboard</h1>
          <p class="text-sm text-navy/60 mb-8">${state.currentUser.email}</p>

          <h2 class="font-display font-bold text-lg border-b border-navy/20 pb-2 mb-4">My Private Annotations (${userAnnots.length})</h2>
          ${userAnnots.length === 0 ? `<p class="text-sm text-navy/50 italic">You haven't saved any highlights or annotations yet.</p>` : `
            <div class="space-y-4">
              ${userAnnots.map(a => `
                <div class="bg-white p-4 rounded border border-navy/10 shadow-sm">
                  <span class="text-xs text-navy/40">${a.date}</span>
                  <p class="font-serif text-sm font-bold text-navy/90 mt-1 mb-2 border-l-2 border-amber-400 pl-3">"${a.text}"</p>
                  <p class="text-sm bg-cream-muted p-2.5 rounded text-navy/80 font-sans">${a.note}</p>
                </div>
              `).join('')}
            </div>
          `}
        </div>
      `;
    }

    function renderAdmin() {
      if (!state.currentUser || state.currentUser.role !== 'admin') {
        return `<p class="text-center py-12">Access Denied. Administrator privileges required.</p>`;
      }
      return `
        <div class="max-w-3xl mx-auto">
          <h1 class="font-serif text-3xl font-bold mb-6">Editorial Publishing Dashboard</h1>
          <form onsubmit="handlePublish(event)" class="space-y-4 bg-white p-6 rounded border border-navy/10">
            <div>
              <label class="block text-xs font-bold uppercase tracking-wider mb-1">Article Title</label>
              <input type="text" id="pub-title" required class="w-full border border-navy/20 p-2 rounded text-sm"/>
            </div>
            <div>
              <label class="block text-xs font-bold uppercase tracking-wider mb-1">Category</label>
              <select id="pub-cat" class="w-full border border-navy/20 p-2 rounded text-sm">
                <option>Law</option>
                <option>Politics</option>
                <option>International Affairs</option>
              </select>
            </div>
            <div>
              <label class="block text-xs font-bold uppercase tracking-wider mb-1">Content</label>
              <textarea id="pub-content" rows="6" required class="w-full border border-navy/20 p-2 rounded text-sm"></textarea>
            </div>
            <button type="submit" class="bg-navy text-cream px-6 py-2 rounded text-xs font-bold tracking-wider uppercase">Publish Article</button>
          </form>
        </div>
      `;
    }

    function renderPigeon() {
      return `
        <div class="max-w-xl mx-auto text-center py-12">
          <h1 class="font-display text-3xl font-bold mb-3">Become a Polity Pigeon</h1>
          <p class="font-serif text-navy/70 mb-6">Join our subscriber network for regular legal analysis and new lesson updates delivered directly to your inbox.</p>
          <form onsubmit="alert('Thank you for subscribing!'); event.preventDefault();" class="flex gap-2">
            <input type="email" placeholder="Enter your student email" required class="flex-grow border border-navy/20 p-3 rounded text-sm" />
            <button class="bg-navy text-cream px-6 py-3 rounded text-xs font-bold tracking-wider uppercase hover:bg-navy-light transition">Subscribe</button>
          </form>
        </div>
      `;
    }

    function handlePublish(e) {
      e.preventDefault();
      const title = document.getElementById('pub-title').value;
      const category = document.getElementById('pub-cat').value;
      const content = document.getElementById('pub-content').value;

      state.articles.unshift({
        id: 'op' + Date.now(),
        title,
        subtitle: content.substring(0, 80) + '...',
        author: state.currentUser.name,
        category,
        date: 'Just Now',
        readTime: '3 min read',
        content
      });

      alert('Article published successfully!');
      navigate('op-eds');
    }

    // --- INITIAL RENDER ---
    render();
  </script>
</body>
</html>
