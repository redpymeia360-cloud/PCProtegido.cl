const GROUP_LINKS = {
  'contacto-general': 'https://chat.whatsapp.com/F1AK1zsW9TlLWv2RzsPxVZ?s=sw&p=i&ilr=1',
  'soporte-general': 'https://chat.whatsapp.com/GygQDwCU1VKDwCBrHrIP0w?s=sw&p=i&ilr=1',
  'planes': 'https://chat.whatsapp.com/Bqyp36i898x28mWocy4NpF?s=sw&p=i&ilr=1'
};

const WHATSAPP_DIRECT = 'https://wa.me/56921733645';

const menuToggle = document.getElementById('menuToggle');
const mainMenu = document.getElementById('mainMenu');
const year = document.getElementById('year');
if (year) year.textContent = new Date().getFullYear();

menuToggle?.addEventListener('click', () => {
  const isOpen = mainMenu.classList.toggle('open');
  menuToggle.setAttribute('aria-expanded', String(isOpen));
});

mainMenu?.querySelectorAll('a').forEach(link => {
  link.addEventListener('click', () => {
    mainMenu.classList.remove('open');
    menuToggle?.setAttribute('aria-expanded', 'false');
  });
});

document.querySelectorAll('[data-plan]').forEach(button => {
  button.addEventListener('click', () => {
    const planSelect = document.getElementById('planSelect');
    if (planSelect) {
      const plan = button.getAttribute('data-plan');
      const option = Array.from(planSelect.options).find(opt => opt.textContent.includes(plan) || plan.includes(opt.textContent));
      if (option) planSelect.value = option.value;
    }
  });
});

function getValue(form, name) {
  return (form.elements[name]?.value || '').trim();
}

function buildMessage(form) {
  const tipo = getValue(form, 'tipoFormulario');
  const nombre = getValue(form, 'nombre');
  const apellido = getValue(form, 'apellido');
  const correo = getValue(form, 'correo');
  const whatsapp = getValue(form, 'whatsapp');
  const empresa = getValue(form, 'empresa');
  const plan = getValue(form, 'plan');
  const mensaje = getValue(form, 'mensaje');

  return `Hola PC Protegido.cl, solicito información.\n\n` +
    `Formulario: ${tipo}\n` +
    `Nombre: ${nombre} ${apellido}\n` +
    `Correo: ${correo}\n` +
    `WhatsApp: ${whatsapp}\n` +
    (empresa ? `Empresa/Institución: ${empresa}\n` : '') +
    `Plan o servicio: ${plan}\n` +
    (mensaje ? `Mensaje: ${mensaje}\n` : '') +
    `\nQuedo atento/a para coordinar atención, valores accesibles y disponibilidad.`;
}

async function copyMessage(text) {
  try {
    await navigator.clipboard.writeText(text);
    return true;
  } catch (error) {
    const temp = document.createElement('textarea');
    temp.value = text;
    document.body.appendChild(temp);
    temp.select();
    const ok = document.execCommand('copy');
    temp.remove();
    return ok;
  }
}

function openWhatsappGroup(target, message) {
  const groupUrl = GROUP_LINKS[target] || GROUP_LINKS['contacto-general'];
  window.open(groupUrl, '_blank', 'noopener,noreferrer');
  const directLink = `${WHATSAPP_DIRECT}?text=${encodeURIComponent(message)}`;
  return directLink;
}

document.querySelectorAll('.contact-form').forEach(form => {
  form.addEventListener('submit', async (event) => {
    event.preventDefault();
    if (!form.reportValidity()) return;

    const status = form.querySelector('.form-status');
    const message = buildMessage(form);
    const copied = await copyMessage(message);
    const directLink = openWhatsappGroup(form.dataset.target, message);

    if (status) {
      status.innerHTML = copied
        ? `Mensaje copiado. Se abrió el grupo de WhatsApp para pegar y enviar. <a href="${directLink}" target="_blank" rel="noopener">Enviar también al WhatsApp directo</a>.`
        : `Se abrió WhatsApp. Si el mensaje no se copió, usa este enlace directo: <a href="${directLink}" target="_blank" rel="noopener">Enviar WhatsApp</a>.`;
    }
  });
});
