---
title: Débogage/diagnostiquer des Applications Spark
titleSuffix: SQL Server big data clusters
description: Utiliser le serveur d’historique Spark pour déboguer et diagnostiquer des applications Spark en cours d’exécution sur des clusters SQL Server 2019 big data.
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
manager: craigg
ms.date: 12/06/2018
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.custom: seodec18
ms.openlocfilehash: e7444a9f5bcdc480425ba02c8a068831c081b47a
ms.sourcegitcommit: 2de5446fbc57787f18a907dd5deb02a7831ec07d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2019
ms.locfileid: "58860331"
---
# <a name="debug-and-diagnose-spark-applications-on-sql-server-big-data-clusters-in-spark-history-server"></a>Débogage et diagnostiquer des Applications Spark sur des clusters de données volumineuses de SQL Server dans le serveur d’historique Spark

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Cet article fournit des conseils sur l’utilisation du serveur d’historique Spark étendu pour déboguer et diagnostiquer des applications Spark dans un cluster de données volumineuses de SQL Server 2019 (version préliminaire). Ces fonctionnalités de débogage et de diagnostic sont intégrées à un serveur d’historique Spark et alimentées par Microsoft. L’extension inclut les onglets de données et onglet graphique et diagnostic. Dans l’onglet données, les utilisateurs peuvent vérifier les données d’entrée et de sortie du travail Spark. Sous l’onglet graphique, les utilisateurs peuvent vérifier le flux de données et relire le graphique du travail. Dans l’onglet de diagnostic, peut faire référence à un décalage des données, décalage horaire et l’analyse d’utilisation de l’exécuteur.

## <a name="get-access-to-spark-history-server"></a>Accéder au serveur d’historique Spark

L’expérience utilisateur de Spark historique server à partir de l’open source a été amélioré avec plus d’informations, ce qui inclut les données spécifiques à un projet et visualisation interactive des flux de travail graphique et les données pour le cluster de données volumineux. 

### <a name="open-the-spark-history-server-web-ui-by-url"></a>Ouvrez le site Web serveur d’historique Spark UI par URL
Remplacez de serveur d’historique Spark en accédant à l’URL suivante, ouvrez `<Ipaddress>` et `<Port>` avec des informations spécifiques de cluster de données volumineuses. Plus d’informations peuvent être référencés : [Déployer le cluster de données volumineux de SQL Server](quickstart-big-data-cluster-deploy.md)

```
https://<Ipaddress>:<Port>/gateway/default/sparkhistory
```

Le web de serveur d’historique Spark l’interface utilisateur ressemble à :

![Serveur d’historique Spark](./media/apache-azure-spark-history-server/spark-history-server.png)


## <a name="data-tab-in-spark-history-server"></a>Onglet données dans le serveur d’historique Spark
Sélectionnez l’ID de tâche, puis cliquez sur **données** dans le menu de l’outil pour obtenir la vue de données.

+ Vérifier le **entrées**, **sorties**, et **opérations de Table** en sélectionnant les onglets séparément.

    ![Onglets de données de serveur d’historique Spark](./media/apache-azure-spark-history-server/sparkui-data-tabs.png)

+ Copier toutes les lignes en cliquant sur le bouton **copie**.

    ![Copier toutes les lignes](./media/apache-azure-spark-history-server/sparkui-data-copy.png)

+ Enregistrer toutes les données en tant que fichier CSV en cliquant sur le bouton **csv**.

    ![Enregistrer les données au format CSV](./media/apache-azure-spark-history-server/sparkui-data-save.png)

+ Recherche en entrant des mots clés dans le champ **recherche**, le résultat de la recherche s’affichent immédiatement.

    ![Faites une recherche avec les mots clés](./media/apache-azure-spark-history-server/sparkui-data-search.png)

+ Cliquez sur l’en-tête de colonne pour trier la table, cliquez sur le signe plus pour développer une ligne pour afficher plus de détails ou cliquez sur le signe moins pour réduire une ligne.

    ![Fonctionnalités de table de données](./media/apache-azure-spark-history-server/sparkui-data-table.png)

+ Télécharger un fichier unique en cliquant sur le bouton **télécharger partielle** qui placer à droite, puis le fichier sélectionné est téléchargé vers emplacement local. Si le fichier n’existe pas plus, il s’ouvre un nouvel onglet pour afficher les messages d’erreur.

    ![Télécharger une ligne de données](./media/apache-azure-spark-history-server/sparkui-data-download-row.png)

+ Copier le chemin d’accès complet ou chemin d’accès relatif en sélectionnant le **copier le chemin complet**, **copier le chemin relatif** qui se développe à partir du menu de téléchargement. Pour les fichiers de stockage azure data lake, **ouvrir dans l’Explorateur de stockage Azure** lancera l’Explorateur de stockage Azure. Et recherchez le dossier exact lors de la connexion.

    ![Copier un chemin d’accès complet ou relatif](./media/apache-azure-spark-history-server/sparkui-data-copy-path.png)

+ Cliquez sur le nombre, le tableau ci-dessous pour naviguer pages quand trop autant de lignes pour afficher dans une page. 

    ![Page de données](./media/apache-azure-spark-history-server/sparkui-data-page.png)

+ Placez le curseur sur le point d’interrogation en regard des données pour afficher l’info-bulle, ou cliquez sur le point d’interrogation pour obtenir plus d’informations.

    ![Données plus d’informations](./media/apache-azure-spark-history-server/sparkui-data-more-info.png)

+ Envoyer des commentaires avec des problèmes en cliquant sur **envoyez-nous vos commentaires**.

    ![commentaires de graphique](./media/apache-azure-spark-history-server/sparkui-graph-feedback.png)

## <a name="graph-tab-in-spark-history-server"></a>Onglet graphique de serveur d’historique Spark

Sélectionnez l’ID de tâche, puis cliquez sur **Graph** dans le menu de l’outil pour obtenir la vue de graphique de travail.

+ Vérifiez la vue d’ensemble de votre travail par le graphique du travail généré. 

+ Par défaut, il affiche tous les travaux, et il peut être filtré par **ID de tâche**.

    ![ID de tâche de graphique](./media/apache-azure-spark-history-server/sparkui-graph-jobid.png)

+ Nous laissons **progression** comme valeur par défaut. Utilisateur peut vérifier le flux de données en sélectionnant **en lecture** ou ** Written *** dans la liste déroulante des **affichage**.

    ![affichage de graphique](./media/apache-azure-spark-history-server/sparkui-graph-display.png)

    L’affichage du nœud graphique en couleur qui affiche la carte thermique.

    ![carte thermique de graphique](./media/apache-azure-spark-history-server/sparkui-graph-heatmap.png)

+ Lire le travail en cliquant sur le **lecture** bouton et arrêter à tout moment en cliquant sur le bouton Arrêter. La tâche s’affichent dans la couleur à afficher un état différent lors de la lecture :

    + Vert indique une réussite : La tâche terminée avec succès.
    + Orange pour une nouvelle tentative : Instances de tâches ayant échoué, mais n’affectent pas le résultat final de la tâche. Ces tâches avaient dupliquer ou réessayez d’instances qui peuvent réussir plus tard.
    + Bleu pour l’exécution : La tâche est en cours d’exécution.
    + Blanc pour l’attente ou ignoré : La tâche est en attente d’exécution, ou l’étape a ignoré.
    + Échec de rouge pour : La tâche a échoué.

    ![échantillon de couleur de graphique, en cours d’exécution](./media/apache-azure-spark-history-server/sparkui-graph-color-running.png)
 
    L’affichage de la scène ignorée en blanc.
    ![échantillon de couleur du graphique, ignorer](./media/apache-azure-spark-history-server/sparkui-graph-color-skip.png)

    ![échantillon de couleur de graphique, a échoué](./media/apache-azure-spark-history-server/sparkui-graph-color-failed.png)
 
    > [!NOTE]
    > La lecture pour chaque tâche est autorisée. Pour un travail incomplet, la lecture n’est pas pris en charge.


+ Faites défiler pour effectuer un zoom avant en entrée/sortie le graphique du travail, ou cliquez sur **Zoom pour ajuster** afin de pouvoir ajuster à l’écran.
 
    ![zoom du graphique pour ajuster](./media/apache-azure-spark-history-server/sparkui-graph-zoom2fit.png)

+ Placez le curseur sur le nœud de graphique pour afficher l’info-bulle lorsqu’il y a des tâches ayant échoué, puis cliquez sur la scène pour ouvrir la page de l’étape.

    ![info-bulle de graphique](./media/apache-azure-spark-history-server/sparkui-graph-tooltip.png)

+ Dans l’onglet graphique de travail, étapes aura une info-bulle et la petite icône affichées si elles ont des tâches répondent à la ci-dessous les conditions :
    + Décalage des données : taille de lecture de données > taille de toutes les tâches à l’intérieur de cette étape de lecture de données moyen * 2 et les données lues taille > 10 Mo
    + Décalage horaire : durée d’exécution > durée d’exécution moyenne de toutes les tâches à l’intérieur de cette étape * 2 et la durée d’exécution > 2 minutes

    ![icône de décalage du graphique](./media/apache-azure-spark-history-server/sparkui-graph-skew-icon.png)

+ Le nœud de graphique du travail affiche les informations suivantes de chaque étape :
    + ID.
    + Nom ou description.
    + Nombre de total de la tâche.
    + Données lues : taille de lecture de la somme de la taille d’entrée et de lecture aléatoire.
    + Écriture de données : les sommes de taille de sortie et la réorganisation de la taille d’écriture.
    + Durée d’exécution : le délai entre l’heure de début de la première tentative et de durée d’exécution de la dernière tentative.
    + Nombre de lignes : la somme des enregistrements d’entrée, enregistrements de sortie, lecture aléatoire des enregistrements de lecture et lecture aléatoire des enregistrements d’écriture.
    + Progression.

    > [!NOTE]
    > Par défaut, le nœud de graphique du travail affiche des informations à partir de la dernière tentative de chaque étape (à l’exception des temps d’exécution de phase), mais pendant le graphe de lecture nœud affiche les informations de chaque nouvelle tentative.

    > [!NOTE]
    > Taille des données de lecture et d’écriture que nous utilisons 1 Mo = 1 000 Ko = 1 000 * 1 000 octets.

+ Envoyer des commentaires avec des problèmes en cliquant sur **envoyez-nous vos commentaires**.

    ![commentaires de graphique](./media/apache-azure-spark-history-server/sparkui-graph-feedback.png)


## <a name="diagnosis-tab-in-spark-history-server"></a>Onglet de diagnostic dans le serveur d’historique Spark
Sélectionnez l’ID de tâche, puis cliquez sur **diagnostic** dans le menu de l’outil pour obtenir la vue de diagnostic de la tâche. L’onglet de diagnostic inclut **d’asymétrie des données**, **du décalage horaire**, et **analyse de l’utilisation d’exécuteur**.
    
+ Vérifier le **d’asymétrie des données**, **du décalage horaire**, et **analyse de l’utilisation d’exécuteur** en sélectionnant les onglets respectivement.

    ![Onglets de diagnostic](./media/apache-azure-spark-history-server/sparkui-diagnosis-tabs.png)

### <a name="data-skew"></a>Décalage des données
Cliquez sur **d’asymétrie des données** sous l’onglet correspondant décalée de tâches sont affichées selon les paramètres spécifiés. 

+ **Spécifier les paramètres** -la première section affiche les paramètres qui sont utilisés pour détecter le décalage des données. La règle intégrée est : Lecture de données de tâche est supérieure à trois fois de la lecture de données moyenne de la tâche, et la lecture de données de tâche sont de plus de 10 Mo. Si vous souhaitez définir vos propres règles pour les tâches décalées, vous pouvez choisir vos paramètres, le **étape incliné**, et **incliner Char** section est actualisée en conséquence. 

+ **Incliné étape** -la seconde section affiche les étapes qui ont faussé tâches répondant aux critères spécifiés ci-dessus. S’il existe plusieurs tâches décalée d’une phase, la table de phase asymétrique affiche uniquement la tâche plus décalée (par exemple, les données plus grandes pour le décalage des données). 

    ![Section2 d’asymétrie des données](./media/apache-azure-spark-history-server/sparkui-diagnosis-dataskew-section2.png)

+ **Incliner graphique** : quand une ligne dans la table intermédiaire décalage est sélectionnée, affichées dans le graphique de décalage plus de distributions de tâche en fonction des données lues et durée d’exécution. Les tâches décalées sont marqués en rouge et les tâches normales sont marquées en bleu. En termes de performances, le graphique affiche uniquement les tâches d’exemple jusqu'à 100. Les détails de la tâche sont affichés dans le volet de droite en bas.

    ![Section3 d’asymétrie des données](./media/apache-azure-spark-history-server/sparkui-diagnosis-dataskew-section3.png)

### <a name="time-skew"></a>Décalage horaire
Le **du décalage horaire** onglet affiche les tâches décalées en fonction de la durée d’exécution de tâches. 

+ **Spécifier les paramètres** -la première section affiche les paramètres qui sont utilisés pour détecter le décalage horaire. Critères pour détecter le décalage horaire par défaut est : durée d’exécution de tâches est supérieure à trois fois de temps d’exécution moyen et l’heure de la tâche d’exécution est supérieure à 30 secondes. Vous pouvez modifier les paramètres selon vos besoins. Le **étape incliné** et **graphique incliner** afficher les étapes correspondantes et les informations sur les tâches comme le **d’asymétrie des données** onglet ci-dessus.

+ Cliquez sur **du décalage horaire**, résultat filtré s’affiche dans **étape incliné** section selon les paramètres définis dans la section **spécifier les paramètres**. Cliquez sur un élément dans **étape incliné** section, puis le graphique correspondant est rédigé dans section3, et les détails de la tâche sont affichés dans le volet de droite en bas.

    ![Section2 de décalage de temps](./media/apache-azure-spark-history-server/sparkui-diagnosis-timeskew-section2.png)

### <a name="executor-usage-analysis"></a>Analyse de l’utilisation d’exécuteur
Le graphique d’utilisation exécuteur permet de visualiser l’état d’allocation et en cours d’exécution des exécuteur réel du travail Spark.  

+ Cliquez sur **analyse de l’utilisation d’exécuteur**, puis nous brouillon quatre courbes types sur l’utilisation de l’exécuteur. Ils incluent **exécuteurs allouée**, **en cours d’exécution des exécuteurs**, **idle exécuteurs**, et **Instances d’exécuteur Max**. Concernant les exécuteurs alloués, chaque « Exécuteur ajouté » ou un événement « Exécuteur supprimé » augmentera ou diminuera les exécuteurs alloués. Vous pouvez vérifier « Chronologie d’événement » dans l’onglet « Tâches » pour plus de comparaison.

    ![Onglet d’exécuteurs](./media/apache-azure-spark-history-server/sparkui-diagnosis-executors.png)

+ Cliquez sur l’icône de couleur pour sélectionner ou désélectionner le contenu correspondant dans tous les brouillons.

    ![Sélectionnez le graphique](./media/apache-azure-spark-history-server/sparkui-diagnosis-select-chart.png)


## <a name="known-issues"></a>Problèmes connus
Le serveur d’historique Spark présente les problèmes connus suivants :

+ Actuellement, il fonctionne uniquement pour les clusters Spark 2.3.

+ Les données d’entrée/sortie à l’aide de RDD n’apparaîtra pas dans l’onglet données.

## <a name="next-steps"></a>Étapes suivantes

* [Gérer les ressources pour un cluster Spark sur HDInsight](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-resource-manager)
* [Configurer les paramètres Spark](https://docs.microsoft.com/azure/hdinsight/spark/apache-spark-settings)
