# Не приходя в сознание — Рефакторинг в 2026

История смерти и перождения микросервиса в суровую эпоху LLM...

---
А начинается история с архитектуры обработки фактур на Фарпосте

<link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.5.2/css/all.min.css">
<pre class="mermaid">
  sequenceDiagram
    participant User as 👤 Пользователь
    participant Monolith as 🐘 Барахолка (PHP)
    participant Uploader as ☕ Pdf Uploader (Java)
    participant ImageStore as 🗃️ ImageStore (Java)
    User->>+Monolith: 1. Отправляет PDF в диалог
    Note right of User: Барахолка не умеет отображать PDF в диалоге
    Monolith->>+Uploader: 2. Передает PDF на обработку
    Note over Uploader: Конвертация PDF → JPEG
    Uploader->>+ImageStore: 3. Отправляет страницы в JPEG
    ImageStore-->>-Uploader: 4. Возвращает идентификаторы сохраненных картинок
    Uploader-->>-Monolith: 5. Отдаёт идентификаторы барахолке
    Monolith-->>-User: 6. Показывает картинки вместо PDF в диалоге
</pre>
<script src="https://cdn.jsdelivr.net/npm/mermaid@11/dist/mermaid.min.js"></script>
<script>
  mermaid.initialize({ startOnLoad: true, securityLevel: 'loose' });
</script>
