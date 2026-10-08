const sections = [
  {
    id: 'abertura',
    title: 'Abertura',
    question: 'Quando você percebe que Deus já está presente antes mesmo de você falar ou agir?',
    idea: 'A liturgia começa com a consciência de que Deus nos precede. Nossa resposta é entrar no tempo de graça que Ele nos oferece.',
    reflection: 'Que lugar da sua rotina precisa ser acolhido pela presença de Deus? O que hoje precisa ser nomeado como convite para entrar em oração?'
  },
  {
    id: 'reconhecimento',
    title: 'Reconhecimento',
    question: 'O que na sua vida precisa ser confessado, acolhido e transformado pela misericórdia de Deus?',
    idea: 'A verdadeira abertura do coração não é negar a fragilidade, mas reconhecer o que procura ser curado pela graça.',
    reflection: 'Você consegue se aproximar de Deus sem esconder o que está pesado? Qual parte da sua história pede acolhimento e cura?'
  },
  {
    id: 'palavra',
    title: 'Palavra',
    question: 'Qual palavra de Deus parece falar diretamente à situação que você vive hoje?',
    idea: 'A Palavra não é apenas informação: ela é presença e direção. A liturgia nos ensina a escutar com o coração disposto.',
    reflection: 'Que frase ou imagem da Palavra está sendo plantada em você? O que essa palavra pede que você viva concretamente?'
  },
  {
    id: 'oferta',
    title: 'Oferta',
    question: 'Em que área da sua vida você pode responder com disponibilidade ao chamado de Deus?',
    idea: 'A oferta pessoal é o gesto concreto de dizer: “Senhor, eu quero participar do que Tu estás fazendo.”',
    reflection: 'O que você precisa entregar, liberar ou confiar para que a sua resposta seja mais verdadeira e generosa?'
  },
  {
    id: 'encaminhamento',
    title: 'Encaminhamento',
    question: 'Como você vai levar esta experiência para o resto do dia, da semana e da vida?',
    idea: 'A liturgia não termina quando a reunião acaba. Ela continua quando a resposta de fé se torna prática, cotidiana e obediente.',
    reflection: 'Qual é o próximo passo concreto que a graça está pedindo de você hoje?'
  }
];

const state = {
  currentIndex: 0,
  theme: localStorage.getItem('liturgia-theme') || 'light'
};

function initialize() {
  applyTheme();
  renderNav();
  renderSections();
  bindNotes();
  bindThemeToggle();
  bindModal();
}

function renderNav() {
  const nav = document.getElementById('chapterNav');
  if (!nav) return;

  nav.innerHTML = sections
    .map((section, index) => {
      const activeClass = index === state.currentIndex ? 'is-active' : '';
      return `
        <button
          type="button"
          class="chapter-button ${activeClass}"
          data-index="${index}"
          aria-label="Ir para a etapa ${index + 1}: ${section.title}"
          aria-pressed="${index === state.currentIndex ? 'true' : 'false'}"
        >
          ${index + 1}
        </button>
      `;
    })
    .join('');

  nav.querySelectorAll('.chapter-button').forEach((button) => {
    button.addEventListener('click', () => {
      state.currentIndex = Number(button.dataset.index);
      renderNav();
      renderSections();
      document.getElementById('content')?.scrollIntoView({ behavior: 'smooth', block: 'start' });
    });
  });
}

function renderSections() {
  const content = document.getElementById('content');
  if (!content) return;

  const template = document.getElementById('sectionTemplate');
  if (!template) return;

  content.innerHTML = '';

  sections.forEach((section, index) => {
    const fragment = template.content.cloneNode(true);
    const article = fragment.querySelector('.step');
    const stepIndex = fragment.querySelector('.step-index');
    const title = fragment.querySelector('.step-title');
    const promptText = fragment.querySelector('.prompt-text');
    const ideaText = fragment.querySelector('.idea-text');
    const reflectionText = fragment.querySelector('.reflection-text');
    const ideaToggle = fragment.querySelector('.idea-toggle');
    const ideaBlock = fragment.querySelector('.idea-content');

    stepIndex.textContent = `Etapa ${index + 1}`;
    title.textContent = section.title;
    promptText.textContent = section.question;
    ideaText.textContent = section.idea;
    reflectionText.textContent = section.reflection;

    if (index !== state.currentIndex) {
      article.setAttribute('hidden', 'hidden');
    }

    ideaToggle.addEventListener('click', () => {
      const isOpen = !ideaBlock.hasAttribute('hidden');
      ideaBlock.toggleAttribute('hidden', isOpen);
      ideaToggle.setAttribute('aria-expanded', String(!isOpen));
      ideaToggle.textContent = isOpen ? 'Ver a ideia central' : 'Ocultar a ideia central';
    });

    ideaToggle.setAttribute('aria-expanded', 'false');
    content.appendChild(fragment);
  });
}

function bindNotes() {
  const notes = document.getElementById('notes');
  const clearButton = document.getElementById('clearNotes');
  if (!notes) return;

  try {
    const saved = localStorage.getItem('liturgia-notes');
    if (saved) {
      notes.value = saved;
    }
  } catch (error) {
    console.warn('Não foi possível carregar as anotações salvas.', error);
  }

  notes.addEventListener('input', () => {
    try {
      localStorage.setItem('liturgia-notes', notes.value);
    } catch (error) {
      console.warn('Não foi possível salvar as anotações.', error);
    }
  });

  clearButton?.addEventListener('click', () => {
    notes.value = '';
    try {
      localStorage.removeItem('liturgia-notes');
    } catch (error) {
      console.warn('Não foi possível limpar as anotações.', error);
    }
  });
}

function bindThemeToggle() {
  const toggle = document.querySelector('[data-theme-toggle]');
  if (!toggle) return;

  toggle.addEventListener('click', () => {
    state.theme = state.theme === 'light' ? 'dark' : 'light';
    applyTheme();
    try {
      localStorage.setItem('liturgia-theme', state.theme);
    } catch (error) {
      console.warn('Não foi possível persistir o tema.', error);
    }
  });
}

function applyTheme() {
  const root = document.documentElement;
  const toggle = document.querySelector('[data-theme-toggle]');
  const label = toggle?.querySelector('.theme-label');
  const icon = toggle?.querySelector('.theme-icon');

  root.setAttribute('data-theme', state.theme);

  if (toggle) {
    toggle.setAttribute('aria-label', state.theme === 'light' ? 'Alternar para tema escuro' : 'Alternar para tema claro');
  }

  if (icon) {
    icon.textContent = state.theme === 'light' ? '☀️' : '🌙';
  }

  if (label) {
    label.textContent = state.theme === 'light' ? 'Tema' : 'Tema';
  }
}

function bindModal() {
  const modal = document.getElementById('imageModal');
  const closeButton = modal?.querySelector('.modal-close');
  const image = document.getElementById('modalImage');

  document.querySelectorAll('[data-image]').forEach((button) => {
    button.addEventListener('click', () => {
      if (!modal || !image) return;
      image.src = button.dataset.image;
      image.alt = button.dataset.alt || 'Imagem ampliada';
      modal.classList.add('is-open');
      modal.setAttribute('aria-hidden', 'false');
    });
  });

  closeButton?.addEventListener('click', () => closeModal(modal, image));

  modal?.addEventListener('click', (event) => {
    if (event.target === modal) {
      closeModal(modal, image);
    }
  });

  document.addEventListener('keydown', (event) => {
    if (event.key === 'Escape' && modal?.classList.contains('is-open')) {
      closeModal(modal, image);
    }
  });
}

function closeModal(modal, image) {
  modal?.classList.remove('is-open');
  modal?.setAttribute('aria-hidden', 'true');
  if (image) {
    image.src = '';
    image.alt = '';
  }
}

document.addEventListener('DOMContentLoaded', initialize);

window.addEventListener('beforeunload', () => {
  if (document.getElementById('notes')) {
    try {
      localStorage.setItem('liturgia-notes', document.getElementById('notes').value);
    } catch (error) {
      console.warn('Não foi possível salvar as anotações antes de sair.', error);
    }
  }
});

