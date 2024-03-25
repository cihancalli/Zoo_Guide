# Zoo Guide
### Soru : 
Bir hayvanat bahçesindeki hayvanlar hakkındaki bilgileri takip etmek için bir sistem tasarlıyorsunuz.
* Hayvanlar:
* Atlar (atlar, zebralar, eşekler vb.),
* Kedigiller (kaplanlar, aslanlar vb.),
* Kemirgenler (sıçanlar, kunduzlar vb.) gibi gruplardaki türlerle karakterize edilir.
* Hayvanlar hakkında depolanan bilgilerin çoğu tüm gruplamalar için aynıdır.
tür adı, ağırlığı, yaşı vb.
* Sistem ayrıca her hayvan için belirli ilaçların dozajını alabilmeli => getDosage ()
* Sistem Yem verme zamanlarını hesaplayabilmelidir => getFeedSchedule ()
Sistemin bu işlevleri yerine getirme mantığı, her gruplama için farklı olacaktır. Örneğin, atlar için yem verme algoritması farklı olup, kaplanlar için farklı olacaktır.

Polimorfizm modelini kullanarak, yukarıda açıklanan durumu ele almak için bir sınıf diyagramı tasarlayın.

### Sınıf Diyagramı

```bash
Hayvan
    - türAdı: String
    - ağırlık: Float
    - yaş: Int
    
    + getDosage(): Dosage
    + getFeedSchedule(): FeedSchedule

At extends Hayvan
    + getDosage(): AtDosage
    + getFeedSchedule(): AtFeedSchedule

Kedigil extends Hayvan
    + getDosage(): KedigilDosage
    + getFeedSchedule(): KedigilFeedSchedule

Kemirgen extends Hayvan
    + getDosage(): KemirgenDosage
    + getFeedSchedule(): KemirgenFeedSchedule

Dosage
    - ilaçAdı: String
    - doz: Float

FeedSchedule
    - saat: Time
    - miktar: Float

AtDosage extends Dosage
    - özelAtIlaçAdı: String

KedigilDosage extends Dosage
    - özelKedigilIlaçAdı: String

KemirgenDosage extends Dosage
    - özelKemirgenIlaçAdı: String

AtFeedSchedule extends FeedSchedule
    - özelAtYem: String

KedigilFeedSchedule extends FeedSchedule
    - özelKedigilYem: String

KemirgenFeedSchedule extends FeedSchedule
    - özelKemirgenYem: String
```

### Açıklama :

* Hayvan sınıfı, tüm hayvanlar için ortak olan tür adı, ağırlık ve yaş gibi temel bilgileri içerir. Ayrıca, her hayvan için ilaç dozajını (getDosage) ve yem verme programını (getFeedSchedule) hesaplamak için soyut yöntemler de içerir.

* At, Kedigil ve Kemirgen sınıfları, Hayvan sınıfından türeyen ve her hayvan grubu için özel bilgileri ve davranışları içeren alt sınıflardır.

*  Dosage ve FeedSchedule sınıfları, ilaç dozajı ve yem verme programı için temel bilgileri içeren soyut sınıflardır.

*  AtDosage, KedigilDosage ve KemirgenDosage sınıfları, her hayvan grubu için özel ilaç doz bilgilerini içeren alt sınıflardır.

*  AtFeedSchedule, KedigilFeedSchedule ve KemirgenFeedSchedule sınıfları, her hayvan grubu için özel yem verme programı bilgilerini içeren alt sınıflardır.


### Polimorfizm : 

* getDosage ve getFeedSchedule yöntemleri, her alt sınıfta farklı şekilde uygulanarak polimorfizm örneği gösterir. Bu sayede, her hayvan grubu için özel hesaplamalar yapılabilir.

* Dosage ve FeedSchedule sınıfları, alt sınıflara ortak olan temel bilgileri ve davranışları tanımlayarak kod tekrarını önler.

Sınıf diyagramı, hayvanat bahçesindeki hayvanlar hakkında bilgileri takip etmek için gerekli olan tüm temel unsurları ve ilişkileri göstermektedir.