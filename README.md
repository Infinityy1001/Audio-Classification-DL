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
