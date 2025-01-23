// Инициализация элементов
const video = document.getElementById('cameraView');
const canvas = document.getElementById('outputCanvas');
const ctx = canvas.getContext('2d');
let model;

// Шаг 1: Запуск камеры
async function startCamera() {
    try {
        const stream = await navigator.mediaDevices.getUserMedia({
            video: { facingMode: "environment" }
        });
        video.srcObject = stream;
        
        // Установка размеров canvas
        video.onloadedmetadata = () => {
            canvas.width = video.videoWidth;
            canvas.height = video.videoHeight;
            initializeDetection();
        };
    } catch (error) {
        alert('Не удалось получить доступ к камере: ' + error.message);
    }
}

// Шаг 2: Инициализация обнаружения объектов
async function initializeDetection() {
    // Загружаем модель для распознавания объектов
    model = await cocoSsd.load();
    
    // Запускаем обработку кадров
    setInterval(() => {
        processFrame();
    }, 1000); // Обработка 1 кадра в секунду
}

// Шаг 3: Обработка кадра
async function processFrame() {
    // Рисуем текущий кадр на canvas
    ctx.drawImage(video, 0, 0, canvas.width, canvas.height);
    
    // Вариант 1: Поиск QR-кодов
    const qrCode = await scanQRCode();
    if(qrCode) {
        handleQRCode(qrCode);
    }
    
    // Вариант 2: Поиск объектов
    const predictions = await model.detect(canvas);
    handleObjects(predictions);
}

// Функция для сканирования QR-кода
async function scanQRCode() {
    const imageData = ctx.getImageData(0, 0, canvas.width, canvas.height);
    return jsQR(imageData.data, imageData.width, imageData.height);
}

// Обработка найденных объектов
function handleObjects(predictions) {
    predictions.forEach(prediction => {
        if(prediction.score > 0.7) {
            showARLabel(prediction.bbox, prediction.class);
        }
    });
}

// Обработка QR-кода
function handleQRCode(qrData) {
    const resultDiv = document.createElement('div');
    resultDiv.style.position = 'absolute';
    resultDiv.style.color = '#00ff00';
    resultDiv.style.fontSize = '24px';
    resultDiv.textContent = `Найден QR: ${qrData.data}`;
    document.getElementById('arElements').appendChild(resultDiv);
}

// Показ AR-меток
function showARLabel(bbox, label) {
    const [x, y, width, height] = bbox;
    const labelDiv = document.createElement('div');
    labelDiv.style.position = 'absolute';
    labelDiv.style.border = '2px solid #00ff00';
    labelDiv.style.color = '#00ff00';
    labelDiv.style.left = `${x}px`;
    labelDiv.style.top = `${y}px`;
    labelDiv.style.width = `${width}px`;
    labelDiv.style.height = `${height}px`;
    labelDiv.innerHTML = `
        <div style="background: rgba(0,0,0,0.5); padding: 5px;">
            ${label}
        </div>
    `;
    document.getElementById('arElements').appendChild(labelDiv);
}

// Запуск при загрузке страницы
window.onload = startCamera;
