---
title: Soumettre un travail Spark sur des clusters de données volumineuses de SQL Server dans Azure Data Studio
description: Soumettre un travail Spark sur des clusters de données volumineuses de SQL Server dans Azure Data Studio
services: SQL Server 2019 big data cluster spark
ms.service: SQL Server 2019 big data cluster spark
author: jejiang
ms.author: jejiang
ms.reviewer: jroth
ms.custom: ''
ms.topic: conceptual
ms.date: 10/01/2018
ms.openlocfilehash: 93ddd7a049bfadd4b2a3ac9ab9db87742d557f3d
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48796026"
---
# <a name="submit-spark-job-on-sql-server-big-data-clusters-in-azure-data-studio"></a>Soumettre un travail Spark sur des clusters de données volumineuses de SQL Server dans Azure Data Studio

Un des principaux scénarios consiste à soumettre un travail Spark pour SQL Server 2019 CTP 2.0. La fonctionnalité de soumission de travaux Spark vous permet de soumettre des fichiers Jar ou Py locaux avec des références à un cluster de données volumineux de SQL Server 2019. Il vous permet également d’exécuter des fichiers Jar ou Py, ce qui sont trouvent déjà dans le système de fichiers HDFS. 

## <a name="prerequisite"></a>Condition préalable 
Installez les outils de big data pour SQL Server et vous connecter à un cluster Big Data avant d’envoyer le travail Spark. Pour les détails de l’installation, consultez pour créer un lien [déployer Big Data Tools](deploy-big-data-tools.md).

## <a name="open-spark-job-submission-dialog"></a>Ouvrir la boîte de dialogue envoi de travaux Spark
Il existe plusieurs manières d’ouvrir la boîte de dialogue envoi de travail Spark. Les méthodes incluent le tableau de bord, Menu contextuel dans l’Explorateur d’objets et commande lieu d’accueil.

+ Cliquez sur **nouveau travail Spark** dans le tableau de bord pour ouvrir la boîte de dialogue envoi de travail Spark.

    ![Soumettre le menu en cliquant sur le tableau de bord ](./media/submit-spark-job/new-spark-job.png)
 
+ Avec le bouton droit sur le cluster dans l’Explorateur d’objets et sélectionnez **soumettre un travail Spark** dans le menu contextuel. Boîte de dialogue de soumission de travaux Spark se.  
 
    ![Envoyer un menu par cluster de clic droit](./media/submit-spark-job/submit-spark-job.png)

+ Avec le bouton droit sur un fichier Jar/Py dans l’Explorateur d’objets et sélectionnez **soumettre un travail Spark** dans le menu contextuel. Boîte de dialogue envoi de travail Spark avec le champ de fichier Jar/Py pourra être pré-remplie s’ouvre. 
 
    ![Soumettre le menu contextuel fichier](./media/submit-spark-job/submit-spark-job-2.png)

+ Utilisez la commande **soumettre un travail Spark** à partir de la palette de commandes en tapant Ctrl + Maj + P (dans Windows) et Cmd + Maj + P (sur Mac).

    ![Envoyer la palette de commandes de menu dans windows](./media/submit-spark-job/submit-spark-job-3.png)

    ![Envoyer la palette de commandes de menu dans mac](./media/submit-spark-job/submit-spark-job-4.png)
  
 
## <a name="submit-spark-job"></a>Soumettre le travail Spark 
La boîte de dialogue envoi de travaux Spark s’affiche comme suit. Entrez le nom de la tâche, chemin d’accès du fichier JAR/Py, classe principale et autres champs. Le fichier Jar / Py source du fichier peut être local ou à partir de HDFS. Si la tâche a de Spark font référence à des fichiers JAR, Py fichiers ou des fichiers supplémentaires, cliquez sur **avancé** onglet et entrez les chemins d’accès de fichier correspondant. Cliquez sur **Submit** pour soumettre le travail Spark.
 
![Nouvelle boîte de dialogue de travail spark](./media/submit-spark-job/submit-spark-job-section.png)

![Boîte de dialogue Avancé](./media/submit-spark-job/submit-spark-job-section-1.png)

## <a name="monitor-spark-job-submission"></a>Surveiller la soumission de travaux Spark
Une fois le travail Spark est envoyé, les informations d’état Spark travail soumission et l’exécution sont affichés dans l’historique des tâches sur la gauche. Et plus d’informations sur la progression et les journaux sont également affichés dans le **sortie** fenêtre en bas.
+ Lorsque le travail Spark est en cours d’exécution, le **l’historique des tâches** panneau et **sortie** fenêtre sont l’actualisation avec la progression.

![Travail du moniteur de spark en cours](./media/submit-spark-job/monitor-spark-job-submission.png)

+ Lorsque le travail Spark est en terminée avec succès, vous pouvez voir des liens de l’interface utilisateur Spark et l’interface utilisateur Yarn dans le **sortie** fenêtre. Vous pouvez cliquer sur les liens pour plus d’informations.

![Lien vers le travail Spark dans la sortie](./media/submit-spark-job/monitor-spark-job-submission-2.png)

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur le cluster de données volumineux de SQL Server et les scénarios associés, consultez [What ' s cluster de données volumineux de SQL Server](big-data-cluster-overview.md)?

