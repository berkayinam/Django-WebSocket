# Django-WebSocket

WebSocket teknolojisini öğrenmek amacıyla geliştirilmiş örnek bir Django projesi.

## 🚀 Proje Hakkında

Bu proje, Django ve WebSocket teknolojilerini kullanarak gerçek zamanlı web uygulamaları geliştirmeyi öğrenmek için oluşturulmuş bir eğitim projesidir. WebSocket protokolünün temel prensiplerini ve Django ile entegrasyonunu göstermektedir.

## 💻 Teknolojiler

### Backend
- Python 3.x
- Django
- Django Channels
- Redis (WebSocket backend)
- ASGI (Asynchronous Server Gateway Interface)

### Frontend
- HTML5
- JavaScript
- WebSocket API
- Bootstrap

## 🛠️ Kurulum

### Gereksinimler
- Python 3.8 veya üzeri
- Redis Server
- pip (Python paket yöneticisi)

### Yerel Geliştirme Ortamı

1. Projeyi klonlayın:
```bash
git clone https://github.com/[kullanıcı-adı]/Django-WebSocket.git
cd Django-WebSocket
```

2. Sanal ortam oluşturun:
```bash
python -m venv venv
source venv/bin/activate  # Linux/macOS
# veya
.\venv\Scripts\activate  # Windows
```

3. Bağımlılıkları yükleyin:
```bash
pip install -r requirements.txt
```

4. Redis sunucusunu başlatın:
```bash
redis-server
```

5. Veritabanını hazırlayın:
```bash
python manage.py migrate
```

6. Geliştirme sunucusunu başlatın:
```bash
python manage.py runserver
```

## 📝 Özellikler

### WebSocket Özellikleri
- [x] Gerçek zamanlı mesajlaşma
- [x] Otomatik bağlantı yönetimi
- [x] Bağlantı durumu takibi
- [x] Hata yönetimi

### Örnek Uygulamalar
- [x] Canlı sohbet odası
- [x] Gerçek zamanlı bildirimler
- [x] Veri akışı gösterimi
- [x] Kullanıcı durumu takibi

## 🔧 WebSocket Yapılandırması

### Django Channels Kurulumu
```python
# settings.py
INSTALLED_APPS = [
    'channels',
    ...
]

ASGI_APPLICATION = 'myproject.asgi.application'

CHANNEL_LAYERS = {
    'default': {
        'BACKEND': 'channels_redis.core.RedisChannelLayer',
        'CONFIG': {
            "hosts": [('127.0.0.1', 6379)],
        },
    },
}
```

### WebSocket Consumer Örneği
```python
# consumers.py
class ChatConsumer(WebsocketConsumer):
    def connect(self):
        self.accept()

    def disconnect(self, close_code):
        pass

    def receive(self, text_data):
        text_data_json = json.loads(text_data)
        message = text_data_json['message']

        self.send(text_data=json.dumps({
            'message': message
        }))
```

## 📚 Öğrenme Kaynakları

- [Django Channels Dokümantasyonu](https://channels.readthedocs.io/)
- [WebSocket API MDN Dokümantasyonu](https://developer.mozilla.org/en-US/docs/Web/API/WebSocket)
- [ASGI Hakkında](https://asgi.readthedocs.io/en/latest/)

## 🐛 Yaygın Sorunlar ve Çözümleri

### Bağlantı Sorunları
- Redis sunucusunun çalıştığından emin olun
- ALLOWED_HOSTS ayarlarını kontrol edin
- WebSocket URL'sinin doğru olduğunu doğrulayın

### Performans İyileştirmeleri
- Redis bağlantı havuzu kullanın
- Mesaj boyutlarını optimize edin
- Gereksiz bağlantıları kapatın

## 🚀 Production Ortamına Geçiş

1. ASGI sunucusu kurun:
```bash
pip install daphne
```

2. Production ayarlarını yapılandırın:
```python
# settings.py
CHANNEL_LAYERS = {
    'default': {
        'BACKEND': 'channels_redis.core.RedisChannelLayer',
        'CONFIG': {
            "hosts": [os.environ.get('REDIS_URL', 'redis://localhost:6379')],
        },
    },
}
```

3. Sunucuyu başlatın:
```bash
daphne -b 0.0.0.0 -p 8000 myproject.asgi:application
```

## 📈 Gelecek Geliştirmeler

- [ ] Otomatik yeniden bağlanma mekanizması
- [ ] WebSocket mesaj sıkıştırma
- [ ] Gelişmiş hata ayıklama araçları
- [ ] Test kapsamının artırılması

## 👥 Katkıda Bulunma

1. Bu repository'yi fork edin
2. Yeni bir branch oluşturun (`git checkout -b feature/AmazingFeature`)
3. Değişikliklerinizi commit edin (`git commit -m 'Add some AmazingFeature'`)
4. Branch'inizi push edin (`git push origin feature/AmazingFeature`)
5. Pull Request oluşturun

## 📝 Lisans

Bu proje [MIT](LICENSE) lisansı altında lisanslanmıştır.

---

⭐️ Bu projeyi beğendiyseniz yıldız vermeyi unutmayın!
