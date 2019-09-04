---
title: 'Tutoriel : Créer un modèle de clustering dans python'
description: Dans la troisième partie de cette série de didacticiels en quatre parties, vous allez créer un modèle K-signifiant pour effectuer le clustering en Python avec SQL Server Machine Learning Services.
ms.prod: sql
ms.technology: machine-learning
ms.devlang: python
ms.date: 08/27/2019
ms.topic: tutorial
author: garyericson
ms.author: garye
ms.reviewer: davidph
monikerRange: '>=sql-server-2017||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: e768f213edf27528e38b2f18d719869fbf089f21
ms.sourcegitcommit: ecb19d0be87c38a283014dbc330adc2f1819a697
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70238718"
---
# <a name="tutorial-build-a-clustering-model-in-python-with-sql-server-machine-learning-services"></a>Tutoriel : Créez un modèle de clustering dans Python avec SQL Server Machine Learning Services

Dans la troisième partie de cette série de didacticiels en quatre parties, vous allez créer un modèle K-signifiant dans Python pour effectuer le clustering. Dans la partie suivante de cette série, vous déploierez ce modèle dans une base de données SQL avec SQL Server Machine Learning Services.

Dans cet article, vous allez apprendre à :

> [!div class="checklist"]
> * Définir le nombre de clusters pour un algorithme K-signifiant
> * Effectuer un clustering
> * Analyser les résultats

Dans la [première partie](tutorial-python-clustering-model.md), vous avez installé les composants requis et importé l’exemple de base de données.

Dans la [deuxième partie](tutorial-python-clustering-model-prepare-data.md), vous avez appris à préparer les données à partir d’une base de données SQL pour effectuer le clustering.

Dans la [quatrième partie](tutorial-python-clustering-model-deploy.md), vous apprendrez à créer une procédure stockée dans une base de données SQL qui peut effectuer un clustering dans Python en fonction de nouvelles données.

## <a name="prerequisites"></a>Prérequis

* La troisième partie de ce didacticiel suppose que vous avez rempli les conditions préalables de la [**première partie**](tutorial-python-clustering-model.md)et effectué les étapes de la [**deuxième partie**](tutorial-python-clustering-model-prepare-data.md).

## <a name="define-the-number-of-clusters"></a>Définir le nombre de clusters

Pour créer un cluster de vos données client, vous allez utiliser l’algorithme de clustering **K-signifiant** , l’une des méthodes les plus simples et les plus connues de regroupement de données.
Vous pouvez en savoir plus sur K-signifiant dans [un guide complet sur l’algorithme de clustering k-signifiant](https://www.kdnuggets.com/2019/05/guide-k-means-clustering-algorithm.html).

L’algorithme accepte deux entrées : Les données elles-mêmes et un nombre prédéfini «*k*» représentant le nombre de clusters à générer.
La sortie est de clusters *k* avec les données d’entrée partitionnées entre les clusters.

L’objectif de K-signifiant est de regrouper les éléments en clusters k de telle sorte que tous les éléments du même cluster soient similaires les uns aux autres et, le cas échéant, aux éléments des autres clusters.

Pour déterminer le nombre de clusters à utiliser pour l’algorithme, utilisez un tracé du dans des groupes somme des carrés, par nombre de clusters extraits. Le nombre approprié de clusters à utiliser se trouve au pli ou au coude du tracé.

```python
################################################################################################
## Determine number of clusters using the Elbow method
################################################################################################

cdata = customer_data
K = range(1, 20)
KM = (sk_cluster.KMeans(n_clusters=k).fit(cdata) for k in K)
centroids = (k.cluster_centers_ for k in KM)

D_k = (sci_distance.cdist(cdata, cent, 'euclidean') for cent in centroids)
dist = (np.min(D, axis=1) for D in D_k)
avgWithinSS = [sum(d) / cdata.shape[0] for d in dist]
plt.plot(K, avgWithinSS, 'b*-')
plt.grid(True)
plt.xlabel('Number of clusters')
plt.ylabel('Average within-cluster sum of squares')
plt.title('Elbow for KMeans clustering')
plt.show()
```

![Graphique coudé](./media/python-tutorial-elbow-graph.png)

Selon le graphique, il semble que *k = 4* serait une bonne valeur à essayer. Cette valeur *k* regroupera les clients en quatre clusters.

## <a name="perform-clustering"></a>Effectuer un clustering

Dans le script Python suivant, vous allez utiliser la fonction KMeans du package sklearn.

```python
################################################################################################
## Perform clustering using Kmeans
################################################################################################

# It looks like k=4 is a good number to use based on the elbow graph.
n_clusters = 4

means_cluster = sk_cluster.KMeans(n_clusters=n_clusters, random_state=111)
columns = ["orderRatio", "itemsRatio", "monetaryRatio", "frequency"]
est = means_cluster.fit(customer_data[columns])
clusters = est.labels_
customer_data['cluster'] = clusters

# Print some data about the clusters:

# For each cluster, count the members.
for c in range(n_clusters):
    cluster_members=customer_data[customer_data['cluster'] == c][:]
    print('Cluster{}(n={}):'.format(c, len(cluster_members)))
    print('-'* 17)
print(customer_data.groupby(['cluster']).mean())
```

## <a name="analyze-the-results"></a>Analyser les résultats

Maintenant que vous avez effectué le clustering à l’aide de K-moyens, l’étape suivante consiste à analyser le résultat et à déterminer si vous pouvez trouver des informations actionnables.

Examinez les valeurs moyennes des clusters et les tailles de cluster imprimées à partir du script précédent.

```results
Cluster0(n=31675):
-------------------
Cluster1(n=4989):
-------------------
Cluster2(n=1):
-------------------
Cluster3(n=671):
-------------------

         customer  orderRatio  itemsRatio  monetaryRatio  frequency
cluster
0        50854.809882    0.000000    0.000000       0.000000   0.000000
1        51332.535779    0.721604    0.453365       0.307721   1.097815
2        57044.000000    1.000000    2.000000     108.719154   1.000000
3        48516.023845    0.136277    0.078346       0.044497   4.271237
```

Les quatre moyennes du cluster sont fournies à l’aide des variables définies dans la [première partie](tutorial-python-clustering-model-prepare-data.md#separate-customers):

* *orderRatio* = ratio d’ordre de retour (nombre total de commandes partiellement ou entièrement retournées par rapport au nombre total de commandes)
* *itemsRatio* = ratio d’élément retourné (nombre total d’éléments retournés par rapport au nombre d’articles achetés)
* *monetaryRatio* = ratio des montants renvoyés (nombre total d’articles retournés par rapport au montant acheté)
* *Frequency* = fréquence de retour

L’exploration de données à l’aide de K-signifiant nécessite souvent une analyse plus approfondie des résultats et des étapes supplémentaires pour mieux comprendre chaque cluster, mais cela peut fournir des bons bons.
Voici quelques façons d’interpréter ces résultats :

* Le cluster 0 semble être un groupe de clients qui ne sont pas actifs (toutes les valeurs sont égales à zéro).
* Le cluster 3 semble être un groupe qui correspond au comportement de retour.

Le cluster 0 est un ensemble de clients qui ne sont manifestement pas actifs. Vous pouvez peut-être cibler des efforts marketing vers ce groupe pour déclencher un intérêt pour les achats. À l’étape suivante, vous allez interroger la base de données sur les adresses de messagerie des clients dans le cluster 0, afin de pouvoir y envoyer un e-mail marketing.

## <a name="clean-up-resources"></a>Supprimer des ressources

Si vous n’allez pas poursuivre ce didacticiel, supprimez la base de données tpcxbb_1gb de SQL Server.

## <a name="next-steps"></a>Étapes suivantes

Dans la troisième partie de cette série de didacticiels, vous avez effectué les étapes suivantes :

* Définir le nombre de clusters pour un algorithme K-signifiant
* Effectuer un clustering
* Analyser les résultats

Pour déployer le modèle de Machine Learning que vous avez créé, suivez la quatrième partie de cette série de didacticiels :

> [!div class="nextstepaction"]
> [Tutoriel : Déployez un modèle de clustering dans Python avec SQL Server Machine Learning Services](tutorial-python-clustering-model-deploy.md)