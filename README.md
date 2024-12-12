# Audio-Classification-DL


### Transformée de Fourier

La transformée de Fourier est une technique mathématique qui permet de décomposer un signal en une somme de sinusoïdes de différentes fréquences. Elle est largement utilisée pour analyser les signaux dans le domaine de la fréquence plutôt que dans le domaine temporel. La transformée de Fourier d'un signal \( f(t) \) est donnée par :

$$ F(\omega) = \int_{-\infty}^{\infty} f(t) e^{-i \omega t} dt $$

#### Propriétés importantes de la transformée de Fourier :
- **Linéarité** : La transformée de Fourier est linéaire, ce qui signifie que si deux signaux sont combinés, la transformée de Fourier de la combinaison est simplement la somme des transformées.
- **Théorème de la convolution** : La convolution dans le domaine temporel correspond à la multiplication dans le domaine de fréquence.
- **Symétrie** : La transformée de Fourier d'un signal réel est généralement complexe et possède une symétrie autour de la fréquence zéro.
- **Transformée inverse** : La transformée de Fourier inverse permet de revenir du domaine fréquentiel au domaine temporel :

$$ f(t) = \frac{1}{2\pi} \int_{-\infty}^{\infty} F(\omega) e^{i \omega t} d\omega $$

#### Applications :
- **Traitement du signal** : Utilisée pour analyser et filtrer des signaux.
- **Compression d'image** : La transformée de Fourier est utilisée dans des techniques comme JPEG.
- **Analyse spectrale** : Pour identifier les fréquences dominantes dans un signal.

---

### Spectrogramme

Un spectrogramme est une représentation visuelle de l'évolution de la densité spectrale de puissance d'un signal en fonction du temps. Il montre comment les différentes fréquences du signal varient au cours du temps.

Le spectrogramme est obtenu en appliquant la **transformée de Fourier courte (STFT)** à un signal. Cela consiste à diviser le signal en segments courts et à appliquer la transformée de Fourier à chaque segment pour observer l'évolution de son contenu fréquentiel au fil du temps.

#### Calcul du spectrogramme :
1. **Fenêtrage** : Le signal est découpé en fenêtres de courte durée (par exemple, à l'aide d'une fenêtre de Hamming, de Hanning, etc.).
2. **Transformée de Fourier courte (STFT)** : Une transformée de Fourier est appliquée à chaque segment de signal, donnant une série de spectres de fréquence au cours du temps.

Le spectrogramme \( S(t, f) \) est donc donné par :

$$ S(t, f) = |\mathcal{F}\{ w(t) \cdot x(t) \} |^2 $$

où \( w(t) \) est la fonction fenêtre, et \( x(t) \) est le signal.

#### Représentation :
Le spectrogramme est généralement affiché sous forme d'une image où :
- **L'axe horizontal (x)** représente le temps.
- **L'axe vertical (y)** représente les fréquences.
- **L'intensité des couleurs** indique la puissance ou l'amplitude de chaque fréquence à un moment donné.

#### Applications :
- **Analyse audio** : Pour visualiser les fréquences présentes dans une chanson ou un son.
- **Traitement du langage** : Utilisé dans la reconnaissance vocale.
- **Analyse des signaux** : Permet de détecter des anomalies ou des changements de fréquence au fil du temps.


### Transformée de Fourier Courte (STFT)

La **Transformée de Fourier Courte (STFT)** est une version de la transformée de Fourier qui permet d'analyser un signal en fonction du temps et de la fréquence. Contrairement à la transformée de Fourier classique qui donne une vue globale du contenu fréquentiel d'un signal sur toute sa durée, la STFT permet d'observer comment les fréquences du signal évoluent au cours du temps.

### Principe de la STFT

L'idée principale de la STFT est de diviser le signal en segments courts (ou fenêtres) et de calculer la transformée de Fourier sur chaque segment. Cela permet de capturer l'évolution des fréquences à différents moments du signal.

La STFT d'un signal \( x(t) \) est définie par :

$$
STFT \{ x(t) \}(t, \omega) = \int_{-\infty}^{\infty} x(\tau) w(\tau - t) e^{-i \omega \tau} d\tau
$$

Où :
- \( t \) est le temps à un instant donné.
- \( \omega \) est la fréquence.
- \( w(\tau - t) \) est la fenêtre temporelle centrée en \( t \), qui permet de limiter l'intégration à une portion finie du signal \( x(t) \).

### Fenêtrage

Le choix de la fenêtre \( w(t) \) est crucial. Elle détermine la durée de l'analyse dans le temps et la précision en fréquence. Les types de fenêtres courants sont :
- **Fenêtre rectangulaire** : Prise en compte de toute la portion de signal sans décalage.
- **Fenêtre de Hamming** : Moins d'artefacts aux bords.
- **Fenêtre de Hanning**, **Fenêtre de Blackman-Harris**, etc. : Offrent de meilleures performances dans certains contextes.

La largeur de la fenêtre joue un rôle important dans le compromis entre la résolution temporelle et la résolution fréquentielle :
- **Fenêtre large** : Bonne résolution fréquentielle, mais moins de précision temporelle.
- **Fenêtre étroite** : Bonne résolution temporelle, mais moins de précision fréquentielle.

### Spectrogramme et STFT

La **STFT** est souvent utilisée pour créer un **spectrogramme**, qui est une représentation visuelle de l'évolution de l'intensité des différentes fréquences dans le signal en fonction du temps. Le spectrogramme est le module au carré de la STFT :

$$
S(t, f) = |STFT\{x(t)\}(t, f)|^2
$$

Cela donne une image où :
- L'axe **horizontal** représente le temps.
- L'axe **vertical** représente les fréquences.
- L'intensité (représentée par des couleurs) indique l'amplitude du signal à une fréquence donnée à un moment donné.

### Applications de la STFT

La STFT est largement utilisée dans de nombreux domaines :
- **Traitement du signal audio** : Pour analyser les fréquences dans un signal audio, comme dans la reconnaissance vocale ou l'analyse musicale.
- **Analyse des vibrations** : Pour observer les changements dans les fréquences d'un signal vibratoire au fil du temps.
- **Compression d'image et de son** : Comme dans le cas du codage audio (MP3) où la STFT permet de traiter les signaux en petites portions.
- **Imagerie médicale** : Utilisée dans des techniques comme l'électroencéphalogramme (EEG) ou l'électrocardiogramme (ECG) pour analyser les signaux physiologiques.

### Résumé

La STFT est un outil fondamental pour l'analyse des signaux non stationnaires, c'est-à-dire les signaux dont les propriétés fréquentielles évoluent avec le temps. Elle permet de comprendre comment les différentes fréquences d'un signal se comportent au fil du temps, ce qui est essentiel dans de nombreuses applications pratiques comme la reconnaissance vocale, la musique, et l'analyse des signaux en général.


### Mel Filterbank

La **Mel Filterbank** est un ensemble de filtres utilisés pour transformer un spectrogramme en une représentation plus adaptée à la perception humaine du son. Elle est principalement utilisée dans le traitement du signal audio, notamment dans les domaines de la reconnaissance vocale, du traitement de la parole et de l'analyse audio.

#### Principe de la Mel Scale

Le système de filtres Mel est basé sur une échelle de fréquence appelée **échelle Mel**, qui est une échelle perceptuelle de fréquence qui imite la manière dont l'oreille humaine perçoit les sons. Sur l'échelle Mel, les fréquences plus basses sont espacées de manière plus large, tandis que les fréquences plus élevées sont plus rapprochées, ce qui correspond à la manière dont nous percevons les changements de fréquence.

L'échelle Mel \( m(f) \) est définie par la relation suivante :

$$
m(f) = 2595 \cdot \log_{10} \left( 1 + \frac{f}{700} \right)
$$

Où :
- \( f \) est la fréquence en Hz.
- \( m(f) \) est la fréquence correspondante sur l'échelle Mel.

Cette relation montre que les fréquences humaines sont perçues de manière logarithmique, ce qui signifie que nous distinguons mieux les basses fréquences et que les hautes fréquences sont perçues avec moins de précision.

#### Fonctionnement de la Mel Filterbank

Une **Mel Filterbank** est une série de filtres (souvent des filtres triangulaires) qui sont espacés sur l'échelle Mel. Chaque filtre de la banque de filtres permet de capturer une plage de fréquences spécifiques, avec une résolution plus fine dans les basses fréquences et une résolution plus grossière dans les hautes fréquences, conformément à la manière dont nous percevons le son.

Le processus de filtrage peut être décrit comme suit :
1. **Spectrogramme** : On commence par appliquer une transformée de Fourier ou une transformée de Fourier courte (STFT) sur un signal audio pour obtenir un spectrogramme, qui est une représentation du signal en fonction du temps et de la fréquence.
2. **Appliquer la Mel Filterbank** : Le spectrogramme est ensuite multiplié par la Mel Filterbank. Chaque filtre capture l'énergie dans une plage de fréquences spécifique sur l'échelle Mel.
3. **Logarithme** : Une fois que l'énergie de chaque bande Mel a été calculée, on applique souvent un logarithme à ces valeurs pour simuler la réponse non linéaire de l'oreille humaine aux variations d'intensité sonore.

Cette représentation est plus adaptée à la reconnaissance et à l'analyse des signaux sonores, car elle est plus proche de la manière dont le système auditif humain perçoit le son.

#### Paramètres d'une Mel Filterbank

- **Nombre de filtres** : Le nombre de filtres dans la banque de filtres Mel est un paramètre important. Plus le nombre de filtres est élevé, plus la représentation sera précise. Dans la pratique, on utilise souvent entre 20 et 40 filtres Mel.
- **Plage de fréquences** : Les filtres couvrent généralement une plage de fréquences qui va de 0 Hz (ou parfois de quelques Hz au minimum) jusqu'à la fréquence de Nyquist, c'est-à-dire la moitié de la fréquence d'échantillonnage du signal audio.

#### Calcul des Coefficients Mel-Frequency Cepstral Coefficients (MFCC)

Les **Mel-Frequency Cepstral Coefficients (MFCC)** sont un ensemble de caractéristiques largement utilisées dans la reconnaissance vocale. Elles sont obtenues en appliquant une Mel Filterbank au spectrogramme, puis en calculant la transformée en cosinus discrète (DCT) des coefficients Mel pour obtenir des caractéristiques compactes. Les MFCC sont souvent utilisés dans les systèmes de reconnaissance vocale pour représenter la texture de la parole.

#### Applications de la Mel Filterbank

- **Reconnaissance vocale** : La Mel Filterbank est couramment utilisée pour extraire des caractéristiques audio pertinentes pour les systèmes de reconnaissance de la parole. Les filtres Mel simulent la manière dont l'oreille humaine perçoit le son, ce qui les rend adaptés pour la reconnaissance vocale.
- **Analyse musicale** : Les banques de filtres Mel sont également utilisées dans l'analyse de la musique, où elles aident à extraire des caractéristiques du timbre musical ou de l'harmonie.
- **Compression audio** : Dans les techniques de compression audio comme MP3, des méthodes similaires à la Mel Filterbank sont utilisées pour extraire des caractéristiques du signal et réduire la quantité de données nécessaires pour représenter le signal.

#### Résumé

La Mel Filterbank est un outil puissant pour transformer un spectrogramme en une représentation perceptuellement plus significative du son. En simulant la façon dont l'oreille humaine perçoit les sons, elle permet de rendre les systèmes de traitement du signal audio plus efficaces et plus adaptés aux applications comme la reconnaissance vocale, l'analyse musicale et la compression audio.
