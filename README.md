# The-Polity-Fold-
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0" />
  <title>The Polity Fold — Publication & Legal Education Platform</title>
  
  <!-- Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="https://fonts.googleapis.com/css2?family=Cinzel:wght@600;700;800&family=Newsreader:ital,opsz,wght@0,6..72,400;0,6..72,500;0,6..72,600;0,6..72,700;1,6..72,400;1,6..72,600&family=Plus+Jakarta+Sans:wght@400;500;600;700&display=swap" rel="stylesheet">
  
  <!-- Tailwind CSS -->
  <script src="https://cdn.tailwindcss.com"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            navy: {
              DEFAULT: '#080E1A',
              paper: '#0F172A',
              soft: '#1E293B',
              border: '#1B2A4A'
            },
            cream: {
              DEFAULT: '#FAF8F5',
              soft: '#F3EFEA',
              muted: '#E6DFD5',
              border: '#D8CFC4'
            },
            accent: {
              gold: '#C59B27',
              highlight: 'rgba(234, 179, 8, 0.35)',
              ink: '#1A2333'
            }
          },
          fontFamily: {
            serif: ['Newsreader', 'Georgia', 'serif'],
            display: ['Cinzel', 'serif'],
            sans: ['Plus Jakarta Sans', '-apple-system', 'sans-serif']
          }
        }
      }
    }
  </script>
  <style>
    body {
      background-color: #FAF8F5;
      color: #080E1A;
      font-feature-settings: "kern", "liga", "clig", "calt", "onum";
    }

    ::selection {
      background-color: rgba(197, 155, 39, 0.35);
      color: #080E1A;
    }

    .border-newspaper {
      border-color: #080E1A;
    }

    .newspaper-grid {
      display: grid;
      grid-template-columns: repeat(12, minmax(0, 1fr));
      gap: 2rem;
    }

    .annotated-text {
      background-color: rgba(234, 179, 8, 0.35);
      border-bottom: 2px solid #C59B27;
      cursor: pointer;
    }

    .dropcap::first-letter {
      font-family: 'Cinzel', serif;
      float: left;
      font-size: 3.75rem;
      line-height: 0.8;
      padding-top: 4px;
      padding-right: 8px;
      padding-bottom: 2px;
      color: #080E1A;
      font-weight: 700;
    }
  </style>
</head>
<body class="bg-cream text-navy font-sans antialiased min-h-screen flex flex-col selection:bg-amber-200">

  <!-- TOP MASTHEAD HEADER -->
  <header class="border-b border-navy bg-cream sticky top-0 z-40">
    <!-- Utility Bar -->
    <div class="border-b border-navy/10 py-1.5 px-4 text-xs font-sans tracking-wide text-navy/70">
      <div class="max-w-7xl mx-auto flex justify-between items-center">
        <div class="flex items-center gap-4">
          <span id="current-date">October 2026</span>
          <span class="hidden sm:inline">•</span>
          <span class="hidden sm:inline">Founder & Editor-in-Chief: <strong>Iligai Taurbek</strong></span>
        </div>
        <div class="flex items-center gap-4" id="header-auth-controls">
          <!-- Rendered via JS -->
        </div>
      </div>
    </div>

    <!-- Main Title Masthead -->
    <div class="max-w-7xl mx-auto px-4 py-6 text-center border-b border-navy/10">
      <a href="#" onclick="navigate('home')" class="inline-block">
        <div class="flex items-center justify-center gap-3 mb-1">
          <svg class="w-7 h-7 text-navy fill-current" viewBox="0 0 24 24">
            <path d="M12 2L2 7l10 5 10-5-10-5zM2 17l10 5 10-5M2 12l10 5 10-5"/>
          </svg>
          <span class="font-display font-bold tracking-widest text-3xl sm:text-4xl text-navy">THE POLITY FOLD</span>
        </div>
        <p class="font-serif italic text-xs sm:text-sm text-navy/70 tracking-wide">A Student Publication & Legal Education Platform</p>
      </a>
    </div>

    <!-- Navigation Menu -->
    <nav class="max-w-7xl mx-auto px-4 flex items-center justify-between text-xs font-semibold tracking-wider uppercase py-2.5 overflow-x-auto">
      <div class="flex items-center space-x-6">
        <button onclick="navigate('home')" class="hover:text-amber-800 transition py-1">Front Page</button>
        <button onclick="navigate('op-eds')" class="hover:text-amber-800 transition py-1">Op-Eds & Commentary</button>
        <button onclick="navigate('law-made-easy')" class="hover:text-amber-800 transition py-1">Law Made Easy</button>
        <button onclick="navigate('contributors')" class="hover:text-amber-800 transition py-1">Contributors</button>
        <button onclick="navigate('pigeon')" class="text-amber-800 hover:underline py-1">Polity Pigeons</button>
      </div>

      <div class="flex items-center space-x-3 pl-4">
        <button onclick="navigate('search')" class="p-1 hover:text-amber-800" title="Search">
          🔍
        </button>
        <div id="admin-badge-slot">
          <!-- Shown when Iligai Taurbek is signed in -->
        </div>
      </div>
    </nav>
  </header>

  <!-- SELECTION TOOLBAR FOR ANNOTATIONS -->
  <div id="annotation-toolbar" class="hidden fixed z-50 bg-navy text-cream px-3 py-1.5 rounded shadow-xl flex items-center space-x-2 text-xs border border-cream/20 font-sans">
    <button onclick="createAnnotation()" class="hover:text-amber-300 font-semibold flex items-center gap-1.5">
      <span>✏️</span> Add Note to Highlight
    </button>
  </div>

  <!-- MAIN CONTENT DISPLAY AREA -->
  <main id="app" class="flex-grow max-w-7xl w-full mx-auto px-4 sm:px-6 lg:px-8 py-8">
    <!-- Pages rendered via JS -->
  </main>

  <!-- FOOTER -->
  <footer class="bg-navy text-cream mt-20 border-t-4 border-accent-gold">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-12">
      <div class="grid grid-cols-1 md:grid-cols-4 gap-8 mb-12">
        <div class="md:col-span-2">
          <h2 class="font-display font-bold text-xl tracking-wider mb-2">THE POLITY FOLD</h2>
          <p class="font-serif italic text-sm text-cream/70 mb-4 max-w-md">An independent, student-led publication and educational platform dedicated to constitutional analysis, jurisprudence, and foreign policy reasoning for young scholars.</p>
          <p class="text-xs text-cream/50 font-sans">Founder & Editor-in-Chief: <strong>Iligai Taurbek</strong></p>
        </div>
        <div>
          <h3 class="font-sans text-xs uppercase tracking-widest font-bold text-accent-gold mb-3">Sections</h3>
          <ul class="space-y-2 text-xs font-sans text-cream/80">
            <li><a href="#" onclick="navigate('op-eds')" class="hover:text-cream">Op-Eds & Analysis</a></li>
            <li><a href="#" onclick="navigate('law-made-easy')" class="hover:text-cream">Law Made Easy</a></li>
            <li><a href="#" onclick="navigate('contributors')" class="hover:text-cream">Contributors</a></li>
            <li><a href="#" onclick="navigate('pigeon')" class="hover:text-cream">Polity Pigeons Newsletter</a></li>
          </ul>
        </div>
        <div>
          <h3 class="font-sans text-xs uppercase tracking-widest font-bold text-accent-gold mb-3">Reader Desk</h3>
          <ul class="space-y-2 text-xs font-sans text-cream/80">
            <li><a href="#" onclick="navigate('dashboard')" class="hover:text-cream">My Annotations Notebook</a></li>
            <li><a href="#" onclick="showSignInModal()" class="hover:text-cream">Account Access</a></li>
            <li><a href="#" onclick="navigate('admin-login')" class="hover:text-cream text-cream/40">Editor Desk (Iligai Taurbek)</a></li>
          </ul>
        </div>
      </div>
      <div class="border-t border-cream/10 pt-6 text-center text-xs text-cream/40 font-sans">
        © 2026 The Polity Fold. All editorial rights reserved.
      </div>
    </div>
  </footer>

  <!-- SIGN IN MODAL -->
  <div id="signin-modal" class="hidden fixed inset-0 z-50 bg-navy/80 backdrop-blur-sm flex items-center justify-center p-4">
    <div class="bg-cream border-2 border-navy max-w-md w-full p-6 sm:p-8 shadow-2xl relative">
      <button onclick="closeSignInModal()" class="absolute top-4 right-4 text-navy/60 hover:text-navy text-xl font-bold">&times;</button>
      
      <div class="text-center mb-6">
        <h2 class="font-display font-bold text-2xl text-navy">SIGN IN TO THE POLITY FOLD</h2>
        <p class="font-serif italic text-xs text-navy/70 mt-1">Access your personal annotation notebook & lesson progress</p>
      </div>

      <div class="space-y-4">
        <div>
          <label class="block text-xs font-bold uppercase tracking-wider mb-1">Your Full Name</label>
          <input type="text" id="user-signin-name" placeholder="e.g. Student Scholar" class="w-full bg-white border border-navy/30 p-2.5 text-sm rounded-none focus:outline-none focus:border-navy" />
        </div>
        <div>
          <label class="block text-xs font-bold uppercase tracking-wider mb-1">Email Address</label>
          <input type="email" id="user-signin-email" placeholder="student@school.edu" class="w-full bg-white border border-navy/30 p-2.5 text-sm rounded-none focus:outline-none focus:border-navy" />
        </div>
        <button onclick="handleUserSignIn()" class="w-full bg-navy text-cream font-bold py-3 text-xs uppercase tracking-widest hover:bg-navy-soft transition">
          Sign In as Student Reader
        </button>
      </div>

      <div class="mt-6 border-t border-navy/10 pt-4 text-center">
        <p class="text-xs text-navy/60">Are you the Editor-in-Chief?</p>
        <button onclick="closeSignInModal(); navigate('admin-login');" class="text-xs font-bold text-amber-800 underline mt-1">
          Iligai Taurbek Admin Portal →
        </button>
      </div>
    </div>
  </div>

  <!-- JAVASCRIPT APP ARCHITECTURE -->
  <script>
    // INITIAL DATA & STORAGE LOGIC
    const STORAGE_KEYS = {
      ARTICLES: 'pf_articles_master',
      LESSONS: 'pf_lessons_master',
      ANNOTATIONS: 'pf_annotations_master',
      USER: 'pf_session_user'
    };

    const initialArticles = [
      {
        id: 'art-1',
        title: 'The Re-Emergence of Stare Decisis in Constitutional Interpretation',
        subtitle: 'Why historical jurisprudence and judicial deference remain fundamental anchors of constitutional stability.',
        category: 'Law',
        author: 'Iligai Taurbek',
        date: 'Oct 2, 2026',
        readTime: '6 min read',
        featured: true,
        content: `The doctrine of stare decisis—derived from the Latin phrase meaning "to stand by things decided"—is far more than a conservative judicial convention. It serves as the institutional bedrock of predictable governance. When courts observe prior rulings, they guarantee that constitutional interpretation reflects enduring legal principles rather than shifting judicial compositions.

In evaluating modern legal controversies, student legal scholars must examine how constitutional jurisprudence balances precedent with corrective justice. Lower courts remain strictly bound by established precedent, preserving constitutional order across state and federal jurisdictions.`
      },
      {
        id: 'art-2',
        title: 'Digital Sovereignty: How Cloud Infrastructure Redefines Foreign Relations',
        subtitle: 'Territorial borders are expanding into server architecture and international data jurisdiction.',
        category: 'International Affairs',
        author: 'Iligai Taurbek',
        date: 'Sep 28, 2026',
        readTime: '5 min read',
        featured: false,
        content: `Across modern diplomatic summits, state jurisdiction over digital infrastructure has emerged as a crucial issue in international relations. As sovereign nations enact local data residency laws, traditional frameworks of public international law face unprecedented stress.

Students analyzing modern foreign affairs must evaluate how electronic data ownership intersects with national security statutes and international trade treaties.`
      }
    ];

    const initialLessons = [
      {
        id: 'les-1',
        course: 'Constitutional Law',
        title: 'Understanding Judicial Review & Marbury v. Madison',
        number: 101,
        difficulty: 'Introductory',
        description: 'Learn how courts evaluate whether legislative statutes or executive actions comply with the supreme law of the land.',
        content: `Judicial review is the authority of courts to review legislative statutes and executive actions, nullifying those that conflict with constitutional principles. Established in the decision of Marbury v. Madison (1803), Chief Justice John Marshall famously asserted that "it is emphatically the province and duty of the judicial department to say what the law is."

To reason like a legal scholar, students must identify: First, the constitutional text at issue; Second, the legislative statute in question; and Third, whether the two can be harmonized without compromising constitutional supremacy.`
      }
    ];

    // APPLICATION STATE
    const state = {
      currentUser: JSON.parse(localStorage.getItem(STORAGE_KEYS.USER)) || null,
      articles: JSON.parse(localStorage.getItem(STORAGE_KEYS.ARTICLES)) || initialArticles,
      lessons: JSON.parse(localStorage.getItem(STORAGE_KEYS.LESSONS)) || initialLessons,
      annotations: JSON.parse(localStorage.getItem(STORAGE_KEYS.ANNOTATIONS)) || [],
      currentView: 'home',
      currentArticleId: null,
      currentLessonId: null
    };

    // SAVE STATE TO LOCAL STORAGE
    function persistData() {
      localStorage.setItem(STORAGE_KEYS.ARTICLES, JSON.stringify(state.articles));
      localStorage.setItem(STORAGE_KEYS.LESSONS, JSON.stringify(state.lessons));
      localStorage.setItem(STORAGE_KEYS.ANNOTATIONS, JSON.stringify(state.annotations));
      if (state.currentUser) {
        localStorage.setItem(STORAGE_KEYS.USER, JSON.stringify(state.currentUser));
      } else {
        localStorage.removeItem(STORAGE_KEYS.USER);
      }
    }

    // NAVIGATION SYSTEM
    function navigate(view, params = {}) {
      state.currentView = view;
      if (params.articleId) state.currentArticleId = params.articleId;
      if (params.lessonId) state.currentLessonId = params.lessonId;
      render();
      window.scrollTo(0, 0);
    }

    // USER & EDITOR AUTHENTICATION
    function showSignInModal() {
      document.getElementById('signin-modal').classList.remove('hidden');
    }

    function closeSignInModal() {
      document.getElementById('signin-modal').classList.add('hidden');
    }

    function handleUserSignIn() {
      const name = document.getElementById('user-signin-name').value.trim();
      const email = document.getElementById('user-signin-email').value.trim();

      if (!name || !email) {
        alert('Please enter your name and email address.');
        return;
      }

      state.currentUser = {
        name,
        email,
        isAdmin: false
      };
      persistData();
      closeSignInModal();
      render();
    }

    function handleAdminLogin(event) {
      event.preventDefault();
      const passcode = document.getElementById('admin-passcode').value;

      // Master passcode for Editor-in-Chief Iligai Taurbek
      if (passcode === 'iligai2026' || passcode === 'admin') {
        state.currentUser = {
          name: 'Iligai Taurbek',
          email: 'iligai.taurbek@polityfold.org',
          isAdmin: true
        };
        persistData();
        navigate('admin-dashboard');
      } else {
        alert('Invalid passcode. Only Founder & Editor-in-Chief Iligai Taurbek has publishing privileges.');
      }
    }

    function signOut() {
      state.currentUser = null;
      persistData();
      navigate('home');
    }

    // ANNOTATION ENGINE
    let selectedRange = null;

    document.addEventListener('selectionchange', () => {
      const selection = window.getSelection();
      const toolbar = document.getElementById('annotation-toolbar');

      if (!state.currentUser) return;
      if (selection.isCollapsed || !selection.toString().trim()) {
        toolbar.classList.add('hidden');
        return;
      }

      const container = document.getElementById('annotatable-content');
      if (container && container.contains(selection.anchorNode)) {
        const range = selection.getRangeAt(0);
        const rect = range.getBoundingClientRect();
        selectedRange = range;

        toolbar.style.top = `${rect.top + window.scrollY - 40}px`;
        toolbar.style.left = `${rect.left + window.scrollX}px`;
        toolbar.classList.remove('hidden');
      } else {
        toolbar.classList.add('hidden');
      }
    });

    function createAnnotation() {
      if (!selectedRange || !state.currentUser) return;
      const text = selectedRange.toString().trim();
      if (!text) return;

      const note = prompt(`Add a personal study note for:\n"${text.substring(0, 50)}..."`);
      if (note !== null) {
        const newAnnot = {
          id: 'note-' + Date.now(),
          userEmail: state.currentUser.email,
          contentId: state.currentArticleId || state.currentLessonId,
          contentType: state.currentArticleId ? 'article' : 'lesson',
          text: text,
          note: note,
          date: new Date().toLocaleDateString('en-US', { month: 'short', day: 'numeric', year: 'numeric' })
        };

        state.annotations.unshift(newAnnot);
        persistData();
        document.getElementById('annotation-toolbar').classList.add('hidden');
        window.getSelection().removeAllRanges();
        render();
      }
    }

    // RENDER CONTROLS
    function renderHeaderAuth() {
      const controls = document.getElementById('header-auth-controls');
      const badgeSlot = document.getElementById('admin-badge-slot');

      if (state.currentUser) {
        if (state.currentUser.isAdmin) {
          badgeSlot.innerHTML = `<button onclick="navigate('admin-dashboard')" class="bg-amber-800 text-cream px-2 py-0.5 rounded text-[10px] font-bold tracking-wider uppercase">Editor Desk</button>`;
        } else {
          badgeSlot.innerHTML = '';
        }

        controls.innerHTML = `
          <button onclick="navigate('dashboard')" class="hover:text-amber-800 font-medium">Notebook (${state.currentUser.name.split(' ')[0]})</button>
          <span>•</span>
          <button onclick="signOut()" class="text-navy/50 hover:text-navy">Sign Out</button>
        `;
      } else {
        badgeSlot.innerHTML = '';
        controls.innerHTML = `
          <button onclick="showSignInModal()" class="hover:text-amber-800 font-medium">Student Sign In</button>
          <span>•</span>
          <button onclick="navigate('admin-login')" class="text-navy/50 hover:text-navy">Editor Login</button>
        `;
      }
    }

    // RENDER APPLICATION VIEWS
    function render() {
      renderHeaderAuth();
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
        case 'contributors':
          app.innerHTML = renderContributors();
          break;
        case 'dashboard':
          app.innerHTML = renderDashboard();
          break;
        case 'admin-login':
          app.innerHTML = renderAdminLogin();
          break;
        case 'admin-dashboard':
          app.innerHTML = renderAdminDashboard();
          break;
        case 'pigeon':
          app.innerHTML = renderPigeon();
          break;
        default:
          app.innerHTML = renderHome();
      }
    }

    // PAGES HTML GENERATORS
    function renderHome() {
      const feat = state.articles.find(a => a.featured) || state.articles[0];
      const recents = state.articles.filter(a => a.id !== feat.id);

      return `
        <!-- FRONT PAGE EDITORIAL HEADER -->
        <div class="border-b-2 border-navy pb-8 mb-10 text-center">
          <p class="font-display text-xs tracking-widest uppercase text-navy/60 mb-2">The Journal of Legal Reasoning & International Policy</p>
          <h1 class="font-serif text-4xl md:text-6xl font-bold tracking-tight text-navy leading-tight mb-3">
            VERITAS ET IUSTITIA
          </h1>
          <p class="font-serif italic text-base text-navy/80 max-w-2xl mx-auto">
            Edited by young scholars, for the next generation of jurists, statesmen, and policy thinkers.
          </p>
        </div>

        <!-- MAIN LAYOUT GRID -->
        <div class="grid grid-cols-1 lg:grid-cols-12 gap-10">
          
          <!-- FEATURED STORY (COL 8) -->
          <div class="lg:col-span-8 border-b lg:border-b-0 lg:border-r border-navy/20 pb-8 lg:pb-0 lg:pr-10">
            <span class="font-sans text-[11px] font-bold uppercase tracking-widest text-amber-800 bg-amber-100/60 px-2 py-0.5 border border-amber-800/20">${feat.category}</span>
            <h2 class="font-serif text-3xl sm:text-4xl font-bold mt-3 mb-3 cursor-pointer hover:text-amber-900 leading-snug" onclick="navigate('article', {articleId: '${feat.id}'})">
              ${feat.title}
            </h2>
            <p class="font-serif text-lg text-navy/80 leading-relaxed mb-4">${feat.subtitle}</p>
            <div class="text-xs font-sans text-navy/60 flex items-center gap-3 border-t border-b border-navy/10 py-2 my-4">
              <span>By <strong>${feat.author}</strong></span>
              <span>•</span>
              <span>${feat.date}</span>
              <span>•</span>
              <span>${feat.readTime}</span>
            </div>
            <p class="font-serif text-base leading-relaxed text-navy/90 dropcap line-clamp-4">
              ${feat.content}
            </p>
            <button onclick="navigate('article', {articleId: '${feat.id}'})" class="mt-4 font-sans text-xs font-bold uppercase tracking-wider text-navy hover:text-amber-800 underline">
              Read Full Commentary →
            </button>
          </div>

          <!-- SIDEBAR / LAW MADE EASY FEATURE (COL 4) -->
          <div class="lg:col-span-4 space-y-8">
            <!-- LAW MADE EASY CALLOUT BOX -->
            <div class="bg-navy text-cream p-6 border-2 border-navy">
              <span class="font-display text-xs text-accent-gold uppercase tracking-widest block mb-1">Educational Platform</span>
              <h3 class="font-display font-bold text-xl text-cream mb-2">LAW MADE EASY</h3>
              <p class="font-serif text-xs text-cream/80 italic mb-4 leading-relaxed">
                Free introductory legal education designed to teach students how judges, attorneys, and scholars actually reason.
              </p>
              <div class="border-t border-cream/20 pt-3 mb-4 space-y-2">
                ${state.lessons.slice(0,2).map(l => `
                  <div class="cursor-pointer hover:text-accent-gold" onclick="navigate('lesson', {lessonId: '${l.id}'})">
                    <p class="font-sans text-xs font-bold text-cream">${l.title}</p>
                    <p class="font-serif text-[11px] text-cream/60">${l.course}</p>
                  </div>
                `).join('')}
              </div>
              <button onclick="navigate('law-made-easy')" class="w-full bg-accent-gold text-navy font-bold py-2 text-xs uppercase tracking-widest hover:bg-amber-300 transition">
                Enter Law School Portal
              </button>
            </div>

            <!-- EDITOR PROFILE -->
            <div class="border border-navy/20 p-5 bg-cream-soft">
              <h4 class="font-display font-bold text-xs uppercase tracking-widest text-navy mb-2">From the Editor-in-Chief</h4>
              <p class="font-serif text-xs text-navy/80 italic leading-relaxed">
                "The Polity Fold was founded on the belief that young minds should engage deeply with jurisprudence, public policy, and legal philosophy before university."
              </p>
              <p class="text-xs font-sans text-navy/60 font-bold mt-2">— Iligai Taurbek</p>
            </div>

          </div>
        </div>

        <!-- RECENT ARTICLES ROW -->
        <div class="mt-16 pt-8 border-t-2 border-navy">
          <h3 class="font-display font-bold text-lg text-navy mb-6 uppercase tracking-wider">Latest Analysis & Commentary</h3>
          <div class="grid md:grid-cols-3 gap-8">
            ${recents.map(a => `
              <div class="border-b md:border-b-0 md:border-r border-navy/10 pb-6 md:pb-0 md:pr-6">
                <span class="font-sans text-[10px] font-bold uppercase tracking-widest text-amber-800">${a.category}</span>
                <h4 class="font-serif text-xl font-bold mt-1 mb-2 cursor-pointer hover:text-amber-800" onclick="navigate('article', {articleId: '${a.id}'})">${a.title}</h4>
                <p class="font-serif text-xs text-navy/70 line-clamp-2 mb-3">${a.subtitle}</p>
                <span class="text-[11px] font-sans text-navy/50">${a.author} •${a.date}</span>
              </div>
            `).join('')}
          </div>
        </div>
      `;
    }

    function renderOpEds() {
      return `
        <div class="border-b-2 border-navy pb-4 mb-8">
          <h1 class="font-serif text-4xl font-bold">Op-Eds & Analysis</h1>
          <p class="font-serif italic text-sm text-navy/70 mt-1">Student-authored legal commentary, foreign affairs, and public policy.</p>
        </div>
        <div class="space-y-8 max-w-4xl">
          ${state.articles.map(a => `
            <div class="border-b border-navy/20 pb-8">
              <div class="flex items-center gap-3 text-xs font-sans mb-1">
                <span class="font-bold text-amber-800 uppercase tracking-widest">${a.category}</span>
                <span>•</span>
                <span class="text-navy/50">${a.date}</span>
              </div>
              <h2 class="font-serif text-2xl font-bold cursor-pointer hover:text-amber-800 mb-2" onclick="navigate('article', {articleId: '${a.id}'})">${a.title}</h2>
              <p class="font-serif text-base text-navy/80 mb-3">${a.subtitle}</p>
              <div class="text-xs font-sans text-navy/60">By <strong>${a.author}</strong> \vert{}${a.readTime}</div>
            </div>
          `).join('')}
        </div>
      `;
    }

    function renderArticle() {
      const art = state.articles.find(a => a.id === state.currentArticleId) || state.articles[0];
      const myAnnots = state.annotations.filter(a => a.contentId === art.id && state.currentUser && a.userEmail === state.currentUser.email);

      return `
        <article class="max-w-3xl mx-auto">
          <div class="border-b border-navy/20 pb-6 mb-8">
            <span class="font-sans text-xs font-bold uppercase tracking-widest text-amber-800">${art.category}</span>
            <h1 class="font-serif text-3xl sm:text-4xl font-bold mt-2 mb-3 text-navy leading-tight">${art.title}</h1>
            <p class="font-serif italic text-lg text-navy/70 mb-4">${art.subtitle}</p>
            <div class="flex items-center justify-between text-xs font-sans text-navy/60 border-t border-b border-navy/10 py-2">
              <span>By <strong>${art.author}</strong></span>
              <span>${art.date} • ${art.readTime}</span>
            </div>
          </div>

          ${state.currentUser ? `
            <div class="bg-amber-50/80 border-l-4 border-accent-gold p-3 mb-6 text-xs font-sans text-amber-900">
              💡 <strong>Annotation Active:</strong> Highlight any passage in the article text below to attach a private study note.
            </div>
          ` : `
            <div class="bg-cream-soft border border-navy/20 p-3 mb-6 text-xs font-sans text-navy/70 flex justify-between items-center">
              <span>Sign in to highlight text and attach private study notes.</span>
              <button onclick="showSignInModal()" class="font-bold underline text-navy">Sign In</button>
            </div>
          `}

          <!-- HIGHLIGHTABLE ARTICLE BODY -->
          <div id="annotatable-content" class="font-serif text-lg leading-relaxed text-navy space-y-6">
            ${art.content.split('\n\n').map(p => `<p>${p}</p>`).join('')}
          </div>

          <!-- USER'S PRIVATE NOTES FOR THIS ARTICLE -->
          ${state.currentUser ? `
            <div class="mt-12 pt-8 border-t-2 border-navy">
              <h3 class="font-display font-bold text-sm uppercase tracking-wider mb-4">Your Annotations for this Article (${myAnnots.length})</h3>${myAnnots.length === 0 ? `<p class="text-xs font-serif italic text-navy/50">You have not created any notes on this text yet.</p>` : `
                <div class="space-y-3">
                  ${myAnnots.map(a => `
                    <div class="bg-cream-soft p-4 border border-navy/10 text-xs font-sans">
                      <p class="font-serif italic font-semibold text-amber-900 border-l-2 border-accent-gold pl-2 mb-2">"${a.text}"</p>
                      <p class="text-navy/90">${a.note}</p>
                    </div>
                  `).join('')}
                </div>
              `}
            </div>
          ` : ''}
        </article>
      `;
    }

    function renderLawMadeEasy() {
      return `
        <div class="border-b-2 border-navy pb-4 mb-8">
          <span class="font-display text-xs font-bold text-accent-gold uppercase tracking-widest">Law School for Students</span>
          <h1 class="font-serif text-4xl font-bold">LAW MADE EASY</h1>
          <p class="font-serif italic text-sm text-navy/70 mt-1">Structured modules teaching secondary students how to analyze legal issues and apply rules to facts.</p>
        </div>

        <div class="grid md:grid-cols-2 gap-8">
          ${state.lessons.map(les => `
            <div class="bg-white p-6 border-2 border-navy shadow-sm flex flex-col justify-between">
              <div>
                <span class="font-sans text-[10px] font-bold uppercase tracking-wider bg-navy text-cream px-2 py-0.5">${les.course}</span>
                <h2 class="font-serif text-xl font-bold mt-3 mb-2">${les.title}</h2>
                <p class="font-serif text-xs text-navy/70 leading-relaxed mb-4">${les.description}</p>
              </div>
              <button onclick="navigate('lesson', {lessonId: '${les.id}'})" class="w-full bg-navy text-cream py-2 text-xs font-bold uppercase tracking-widest hover:bg-navy-soft transition">
                Begin Lesson & Reasoning Exercise →
              </button>
            </div>
          `).join('')}
        </div>
      `;
    }

    function renderLesson() {
      const les = state.lessons.find(l => l.id === state.currentLessonId) || state.lessons[0];
      return `
        <div class="max-w-3xl mx-auto">
          <div class="border-b border-navy/20 pb-4 mb-6">
            <span class="font-sans text-xs font-bold text-amber-800 uppercase tracking-widest">${les.course} • Module ${les.number}</span>
            <h1 class="font-serif text-3xl font-bold mt-1 mb-2">${les.title}</h1>
            <p class="font-serif italic text-sm text-navy/70">${les.description}</p>
          </div>

          <div id="annotatable-content" class="bg-white p-8 border border-navy/20 font-serif text-base leading-relaxed text-navy space-y-4 mb-8">
            ${les.content.split('\n\n').map(p => `<p>${p}</p>`).join('')}
          </div>

          <div class="bg-cream-soft p-6 border-2 border-navy">
            <h3 class="font-display font-bold text-xs uppercase tracking-wider text-navy mb-2">Legal Analysis Challenge</h3>
            <p class="font-serif text-xs text-navy/80 mb-4">How should a court balance executive necessity against statutory rights under this precedent?</p>
            <textarea placeholder="Write your legal rationale here..." class="w-full bg-white border border-navy/30 p-3 text-xs font-sans rounded-none focus:outline-none focus:border-navy"></textarea>
          </div>
        </div>
      `;
    }

    function renderContributors() {
      return `
        <div class="border-b-2 border-navy pb-4 mb-8">
          <h1 class="font-serif text-3xl font-bold">Editorial Masthead & Contributors</h1>
        </div>
        <div class="max-w-xl bg-white p-6 border-2 border-navy">
          <h2 class="font-display font-bold text-lg text-navy">Iligai Taurbek</h2>
          <p class="font-sans text-xs text-amber-800 font-bold uppercase tracking-widest mb-3">Founder & Editor-in-Chief</p>
          <p class="font-serif text-sm text-navy/80 leading-relaxed">
            Iligai Taurbek is a student researcher focusing on constitutional jurisprudence, political science, and legal advocacy. She founded The Polity Fold to create a dedicated scholarly platform for young minds.
          </p>
        </div>
      `;
    }

    function renderDashboard() {
      if (!state.currentUser) {
        return `
          <div class="text-center py-16">
            <h2 class="font-serif text-2xl font-bold mb-2">Sign In Required</h2>
            <p class="font-serif italic text-sm text-navy/70 mb-4">You must be signed in to access your private annotations notebook.</p>
            <button onclick="showSignInModal()" class="bg-navy text-cream px-6 py-2 text-xs font-bold uppercase tracking-widest">Sign In Now</button>
          </div>
        `;
      }

      const myNotes = state.annotations.filter(a => a.userEmail === state.currentUser.email);

      return `
        <div class="max-w-4xl mx-auto">
          <div class="border-b-2 border-navy pb-4 mb-8">
            <h1 class="font-serif text-3xl font-bold">My Personal Annotations Notebook</h1>
            <p class="font-serif italic text-sm text-navy/70 mt-1">Saved highlights and notes for <strong>${state.currentUser.name}</strong> (${state.currentUser.email})</p>
          </div>

          ${myNotes.length === 0 ? `
            <div class="bg-white p-8 border border-navy/20 text-center">
              <p class="font-serif italic text-sm text-navy/60">You have no saved annotations yet. Read any Op-Ed or Law Made Easy lesson, highlight a passage, and add your note.</p>
            </div>
          ` : `
            <div class="space-y-4">
              ${myNotes.map(n => `
                <div class="bg-white p-5 border border-navy/20">
                  <div class="flex justify-between items-center text-[11px] font-sans text-navy/50 mb-2">
                    <span>${n.contentType.toUpperCase()} NOTE</span>
                    <span>${n.date}</span>
                  </div>
                  <p class="font-serif text-sm font-semibold text-amber-900 border-l-2 border-accent-gold pl-3 mb-3">"${n.text}"</p>
                  <p class="font-sans text-xs bg-cream-soft p-3 text-navy/90">${n.note}</p>
                </div>
              `).join('')}
            </div>
          `}
        </div>
      `;
    }

    function renderAdminLogin() {
      return `
        <div class="max-w-md mx-auto py-12">
          <div class="bg-white p-8 border-2 border-navy text-center">
            <h1 class="font-display font-bold text-2xl text-navy mb-1">EDITOR DESK LOGIN</h1>
            <p class="font-serif italic text-xs text-navy/70 mb-6">Restricted publishing access for Founder Iligai Taurbek</p>
            
            <form onsubmit="handleAdminLogin(event)" class="space-y-4 text-left">
              <div>
                <label class="block text-xs font-bold uppercase tracking-wider mb-1">Admin Passcode</label>
                <input type="password" id="admin-passcode" placeholder="Enter Iligai's passcode" required class="w-full bg-cream-soft border border-navy/30 p-2.5 text-sm rounded-none focus:outline-none focus:border-navy" />
              </div>
              <button type="submit" class="w-full bg-navy text-cream font-bold py-3 text-xs uppercase tracking-widest hover:bg-navy-soft transition">
                Authenticate as Editor
              </button>
            </form>
          </div>
        </div>
      `;
    }

    function renderAdminDashboard() {
      if (!state.currentUser || !state.currentUser.isAdmin) {
        return renderAdminLogin();
      }

      return `
        <div class="max-w-4xl mx-auto">
          <div class="border-b-2 border-navy pb-4 mb-8 flex justify-between items-end">
            <div>
              <span class="font-display text-xs text-amber-800 uppercase tracking-widest font-bold">Authorized Editor Portal</span>
              <h1 class="font-serif text-3xl font-bold">Editor Desk — Iligai Taurbek</h1>
            </div>
            <button onclick="signOut()" class="text-xs font-sans text-navy/60 hover:text-navy underline">Sign Out</button>
          </div>

          <!-- PUBLISH NEW ARTICLE FORM -->
          <div class="bg-white p-6 border-2 border-navy mb-10">
            <h2 class="font-display font-bold text-lg text-navy mb-4 border-b border-navy/10 pb-2">Publish New Commentary / Article</h2>
            
            <form onsubmit="handlePublishArticle(event)" class="space-y-4">
              <div class="grid md:grid-cols-2 gap-4">
                <div>
                  <label class="block text-xs font-bold uppercase tracking-wider mb-1">Article Headline</label>
                  <input type="text" id="new-art-title" required class="w-full border border-navy/30 p-2 text-xs" />
                </div>
                <div>
                  <label class="block text-xs font-bold uppercase tracking-wider mb-1">Category</label>
                  <select id="new-art-cat" class="w-full border border-navy/30 p-2 text-xs">
                    <option>Law</option>
                    <option>Politics</option>
                    <option>International Affairs</option>
                    <option>Public Policy</option>
                    <option>Society</option>
                  </select>
                </div>
              </div>

              <div>
                <label class="block text-xs font-bold uppercase tracking-wider mb-1">Subtitle / Abstract</label>
                <input type="text" id="new-art-sub" required class="w-full border border-navy/30 p-2 text-xs" />
              </div>

              <div>
                <label class="block text-xs font-bold uppercase tracking-wider mb-1">Article Body Content</label>
                <textarea id="new-art-body" rows="6" required class="w-full border border-navy/30 p-2 text-xs font-serif"></textarea>
              </div>

              <div class="flex items-center gap-2">
                <input type="checkbox" id="new-art-featured" class="border-navy" />
                <label for="new-art-featured" class="text-xs font-sans">Set as Featured Front-Page Article</label>
              </div>

              <button type="submit" class="bg-navy text-cream font-bold px-6 py-2.5 text-xs uppercase tracking-widest hover:bg-navy-soft transition">
                Publish Article Live
              </button>
            </form>
          </div>

          <!-- MANAGED CONTENT LIST -->
          <div>
            <h3 class="font-display font-bold text-md text-navy mb-3">Published Articles (${state.articles.length})</h3>
            <div class="space-y-2">
              ${state.articles.map(art => `
                <div class="bg-cream-soft p-3 border border-navy/20 flex justify-between items-center text-xs">
                  <div>
                    <span class="font-bold text-navy">${art.title}</span>
                    <span class="text-navy/50 font-sans"> (${art.category})</span>
                  </div>
                  <button onclick="deleteArticle('${art.id}')" class="text-red-700 hover:underline font-sans font-bold">Delete</button>
                </div>
              `).join('')}
            </div>
          </div>
        </div>
      `;
    }

    function renderPigeon() {
      return `
        <div class="max-w-md mx-auto text-center py-12">
          <h1 class="font-display text-3xl font-bold mb-2">BECOME A POLITY PIGEON</h1>
          <p class="font-serif text-sm text-navy/70 mb-6">Receive legal analysis and lesson publications directly in your inbox.</p>
          <form onsubmit="alert('Thank you for subscribing to The Polity Fold.'); event.preventDefault();" class="space-y-3">
            <input type="email" placeholder="Enter your email" required class="w-full border border-navy/30 p-3 text-xs font-sans text-center" />
            <button class="w-full bg-navy text-cream font-bold py-3 text-xs uppercase tracking-widest">Subscribe</button>
          </form>
        </div>
      `;
    }

    // ADMIN ACTION HANDLERS
    function handlePublishArticle(e) {
      e.preventDefault();
      const title = document.getElementById('new-art-title').value.trim();
      const category = document.getElementById('new-art-cat').value;
      const subtitle = document.getElementById('new-art-sub').value.trim();
      const content = document.getElementById('new-art-body').value.trim();
      const featured = document.getElementById('new-art-featured').checked;

      if (featured) {
        state.articles.forEach(a => a.featured = false);
      }

      const newArticle = {
        id: 'art-' + Date.now(),
        title,
        subtitle,
        category,
        author: 'Iligai Taurbek',
        date: new Date().toLocaleDateString('en-US', { month: 'short', day: 'numeric', year: 'numeric' }),
        readTime: '4 min read',
        featured: featured,
        content
      };

      state.articles.unshift(newArticle);
      persistData();
      alert('Article published successfully by Editor Iligai Taurbek.');
      navigate('home');
    }

    function deleteArticle(id) {
      if (confirm('Are you sure you want to delete this article?')) {
        state.articles = state.articles.filter(a => a.id !== id);
        persistData();
        render();
      }
    }

    // INITIAL APP INITIALIZATION
    render();
  </script>
</body>
</html>
