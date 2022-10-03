# Notice technique

Cette notice technique détaille le modèle de tarification utilisée pour estimer le prix d'un contrat d'énergie uniquement électrique dans le cadre du projet [Blent.ai](https://blent.ai).

## Modèle de tarification

Le modèle de tarification est une formule mathématique qui utilise à la fois les informations locales de l'utilisateur (ville, région) et les informations liées au foyer (superficie, usages de l'électricité, nombre de personnes). Dans le cadre du projet, toute autre information n'intervient pas dans le calcul.
La formule suivante est utilisée pour déterminer une estimation de la tarification mensuelle, incluant le prix du contrat.

$$\text{Prix}=(0.1558 + \alpha M) x +C$$

- Le tarif réglementé (à 0,1558€) correspond au prix de base pour chaque kWh.
- $x$ indique le nombre de kWh consommés chaque mois et estimé à partir des informations fournies par l'utilisateur.
- $M$ représente une augmentation du prix comprise entre 0€ et 0.05€, qui dépend de la consommation dans la région les 30 derniers jours. Plus une région a consommé d'électricité au cours du mois derniers, plus la majoration est importante.
- $\alpha$ est un coefficient calculé selon la consommation prévisionnelle annuelle dans la ville, compris entre 1 et 1.2, et mesure l'évolution de la consommation dans la ville. Plus la prévision de la consommation est importante pour l'année suivante, plus la valeur est élevée (bornée à 1.2).
- $C$ est une constante qui correspond au prix du contrat, à savoir 6€ par mois.

Le membre $\alpha M$ représente donc une majoration qui dépend de la consommation locale de l'utilisateur.

Le modèle de tarification proposé se base sur le tableau suivant indiquant les consommations électriques annuelles par an pour chaque usage.

|Usage| Consommation annuelle |
|--|--|
| Chauffage | Environ **110 kWh par mètre carré** |
| Eau chaude | Environ **800 kWh par personne** |
| Cuisson | Environ **200 kWh par personne** |
| Appareils électroménagers et éclairage | Environ **1100 kWh par foyer** |

## Modalités de calcul de la majoration

### Calcul de $\alpha$

La valeur de $\alpha$ se calcule comme étant l'augmentation relative de la prévision annuelle l'année $n+1$ à partir de l'année $n$. 

**Exemple** : si l'année $n+1$, la consommation annuelle est estimée à 407 MWh et que l'année $n$, elle a été relevée à 398 MWh, alors

$$\alpha=1 + \frac{407-398}{398} =1.023$$

Si $\alpha$ dépasse 1.3, la valeur reste au maximum à à ce seuil. À l'inverse, si $\alpha < 1$, alors la valeur est automatiquement ramenée à 1.

### Calcul de $M$

$M$ permet de prendre en compte l'évolution de la demande récente au niveau d'une région particulière. Pour cela, on calcule la consommation moyenne au cours des 30 derniers jours de la région dans laquelle est située la ville de l'utilisateur pour calculer cette quantité.

$$M =\min \left(0.05, 0.01 * \frac{\text{Consommation moyenne sur 30 jours (MWh)}}{4000} \right)$$

Par exemple, la région Nouvelle-Aquitaine a une consommation moyenne sur 30 jours de 4800 MWh, alors $M=0.012€$.

## Exemple de calcul
Par exemple, considérons un logement de 50 mètres carrés avec 2 personnes résidant. Le chauffage et l'eau chaude est électrique, et la cuisson au gaz naturel.

Chaque année, la consommation électrique du foyer est :

- 110 kWh par 50 mètres carrés, soit 5500 kWh annuel pour le chauffage.
- 800 kWh pour deux personnes, soit 1600 kWh annuel pour l'eau chaude.
- 1100 kWh pour les appareils électroménagers et l'éclairage.
- Le foyer ne consomme pas d'électricité pour la cuisson.

La consommation annuelle totale du foyer est donc $x=8200$ kWh. En considérant $\alpha = 1.1$ et $M = 0.012$€, le prix mensuel est de :

$$(0.1558 + 1.1 \times 0.012) \times 8200 / 12 + 8 = 123.5€$$

Soit environ 0.1807€ le kWh.
