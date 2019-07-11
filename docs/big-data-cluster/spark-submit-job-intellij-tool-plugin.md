---
title: Exécuter les travaux Spark dans le Kit de ressources Azure pour IntelliJ sur le cluster de données volumineux de SQL Server
titleSuffix: SQL Server big data clusters
description: Envoyer des travaux Spark sur des clusters de données volumineuses de SQL Server dans le Kit de ressources Azure pour IntelliJ.
author: jejiang
ms.author: jejiang
ms.reviewer: mikeray
ms.date: 02/28/2019
ms.topic: conceptual
ms.prod: sql
ms.technology: big-data-cluster
ms.openlocfilehash: 5d2bb4b55b578530a29490a0a1a284f338686c38
ms.sourcegitcommit: e0c55d919ff9cec233a7a14e72ba16799f4505b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67728370"
---
# <a name="submit-spark-jobs-on-sql-server-big-data-clusters-in-intellij"></a>Envoyer des travaux Spark sur des clusters de données volumineuses de SQL Server dans IntelliJ

[!INCLUDE[tsql-appliesto-ssver15-xxxx-xxxx-xxx](../includes/tsql-appliesto-ssver15-xxxx-xxxx-xxx.md)]

Un des scénarios clés pour les clusters de données volumineuses de SQL Server est la possibilité d’envoyer des travaux Spark. La fonctionnalité de soumission de travaux Spark vous permet de soumettre des fichiers Jar ou Py locaux avec des références à des clusters de données volumineuses de SQL Server. Il vous permet également d’exécuter des fichiers Jar ou Py, ce qui sont trouvent déjà dans le système de fichiers HDFS. 

## <a name="prerequisites"></a>Prérequis

- Cluster de données volumineux de SQL Server.
- Oracle Java Development Kit. Vous pouvez l’installer à partir de la [site Web d’Oracle](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html).
- IntelliJ IDEA. Vous pouvez l’installer à partir de la [site Web de JetBrains](https://www.jetbrains.com/idea/download/).
- Kit de ressources Azure pour IntelliJ extension. Pour obtenir des instructions d’installation, consultez [installer le Kit de ressources pour IntelliJ](https://docs.microsoft.com/azure/azure-toolkit-for-intellij-installation).

## <a name="link-sql-server-big-data-cluster"></a>Cluster de données volumineux de SQL Server de lien
1. Ouvrez l’outil d’IntelliJ IDEA.

2. Si vous utilisez un certificat auto-signé, désactiver la validation du certificat SSL à partir de **outils** menu, sélectionnez **Azure**, **valider le certificat de SSL de Cluster Spark**, puis  **Désactiver**.

    ![lier le cluster de données volumineux de SQL Server - désactiver le protocole SSL](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-disableSSL.png)

3. Ouvrez l’Explorateur Azure à partir de **vue** menu, sélectionnez **Windows de l’outil**, puis sélectionnez **Azure Explorer**.
4. Cliquez avec le bouton droit sur **cluster de données volumineux de SQL Server**, sélectionnez **cluster de données volumineux de lien de SQL Server**. Entrez le **Server**, **nom d’utilisateur**, et **mot de passe**, puis cliquez sur **OK**.

    ![lier un cluster Big Data - boîte de dialogue](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-dialog.png)

5. Lors de la boîte de dialogue de certificat de serveur non autorisé s’affiche, cliquez sur **Accept**. Vous pouvez gérer le certificat ultérieurement, consultez [certificats de serveur](https://www.jetbrains.com/help/idea/settings-tools-server-certificates.html).

6. Le cluster lié répertorie sous **cluster de données volumineux de SQL Server**. Vous pouvez analyser la tâche spark en ouvrant l’interface utilisateur de l’historique spark et l’interface utilisateur Yarn, vous pouvez également dissocier, par le bouton droit sur le cluster.

    ![lien cluster Big Data - menu contextuel](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-contextmenu.png)

## <a name="create-a-spark-scala-application-from-hdinsight-template"></a>Créer une application Spark Scala à partir du modèle de HDInsight

1. Démarrez IntelliJ IDEA et créez un projet. Dans le **nouveau projet** boîte de dialogue, suivez étapes ci-dessous : 

   a. Sélectionnez **Azure Spark/HDInsight** > **Spark du projet avec des exemples (Scala)** .

   b. Dans la liste des **outils de génération**, sélectionnez l’une des options suivantes, en fonction de vos besoins :

      * **Maven**, pour la prise en charge de l’Assistant de création de projets Scala
      * **SBT**, pour gérer les dépendances et la génération du projet Scala

    ![Boîte de dialogue Nouveau projet](./media/spark-submit-job-intellij-tool-plugin/create-hdi-scala-app.png)

2. Sélectionnez **Suivant**.

3. L’Assistant de création de projets Scala détecte automatiquement si vous avez installé le plug-in Scala. Sélectionnez **Installer**.

   ![Vérification du plug-in Scala](./media/spark-submit-job-intellij-tool-plugin/Scala-Plugin-check-Reminder.PNG) 

4. Pour télécharger le plug-in Scala, sélectionnez **OK**. Suivez les instructions pour redémarrer IntelliJ. 

   ![La boîte de dialogue installation plug-in Scala](./media/spark-submit-job-intellij-tool-plugin/Choose-Scala-Plugin.PNG)

5. Dans le **nouveau projet** fenêtre, procédez comme suit :  

    ![Sélection du kit de développement logiciel (SDK) Spark](./media/spark-submit-job-intellij-tool-plugin/hdi-new-project.png)

   a. Entrez un nom de projet et un emplacement.

   b. Dans le **SDK de projet** liste déroulante, sélectionnez **Java 1.8** pour le cluster Spark 2.x, ou sélectionnez **Java 1.7** pour le cluster Spark 1.x.

   c. Dans le **version Spark** liste déroulante, Assistant de création de projets Scala intègre la version correcte pour le Kit de développement logiciel Spark et le SDK Scala. Si la version du cluster spark est antérieure à la version 2.0, sélectionnez **Spark 1.x**. Sinon, sélectionnez **Spark 2.x**. La version utilisée dans cet exemple est **Spark 2.0.2 (Scala 2.11.8)** .

6. Sélectionnez **Terminer**.

7. Le projet Spark crée automatiquement un artefact à votre intention. Pour afficher l’artefact, procédez comme suit :

   a. Sur le **fichier** menu, sélectionnez **Structure de projet**.

   b. Dans le **Structure de projet** boîte de dialogue, sélectionnez **artefacts** pour afficher l’artefact par défaut qui est créé. Vous pouvez également créer votre propre artefact en sélectionnant le signe plus ( **+** ).

      ![Informations sur l’artefact dans la boîte de dialogue](./media/spark-submit-job-intellij-tool-plugin/default-artifact.png)
      

## <a name="submit-application-to-sql-server-big-data-cluster"></a>Soumettre l’application à un cluster de données volumineux de SQL Server
Après le lien d’un cluster de données volumineux de SQL Server, vous pouvez soumettre application vers celle-ci.

1. Définissez la configuration dans **exécuter/déboguer des Configurations** fenêtre, cliquez sur + ->**Apache Spark sur SQL Server**, sélectionnez onglet **exécuter à distance dans le Cluster**, définissez les paramètres en tant que suivant, puis cliquez sur OK.

    ![Console interactive ajouter l’entrée de configuration](./media/spark-submit-job-intellij-tool-plugin/interactive-console-add-config-entry.png)

    ![lien cluster Big Data - config](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-config.png)

    * Pour **Spark clusters (Linux uniquement)** , sélectionnez le cluster sur lequel vous souhaitez exécuter votre application.

    * Sélectionnez un artefact à partir du projet IntelliJ, ou sélectionnez-en un dans le disque dur.

    * **Nom de la classe principale** champ : la valeur par défaut est la classe main du fichier sélectionné. Vous pouvez modifier la classe en sélectionnant les points de suspension ( **...** ) pour choisir une autre classe.   

    * **Configurations de tâche** champ :  Les valeurs par défaut sont définies en tant qu’image indiqué ci-dessus. Vous pouvez modifier la valeur ou ajouter la nouvelle clé/valeur votre soumission de travaux. Pour plus d'informations : [Apache Livy API REST](http://livy.incubator.apache.org./docs/latest/rest-api.html)

      ![La signification configuration travail de boîte de dialogue Spark Submission](./media/spark-submit-job-intellij-tool-plugin/submit-job-configurations.png)

    * **Arguments de ligne de commande** champ : Vous pouvez entrer les valeurs d’arguments fractionner par un espace pour la classe principale, si nécessaire.

    * **Référencées des fichiers JAR** et **fichiers référencés** champs : vous pouvez entrer les chemins des JAR et fichiers référencés, le cas échéant. Pour plus d'informations : [Apache Spark Configuration](https://spark.apache.org/docs/latest/configuration.html#runtime-environment) 

      ![Le fichier jar boîte de dialogue Spark Submission fichiers signification](./media/spark-submit-job-intellij-tool-plugin/jar-files-meaning.png)

       > [!NOTE]  
       > Pour télécharger votre référencé fichiers JAR et les fichiers référencés, reportez-vous à : [Comment charger des ressources en cluster](https://docs.microsoft.com/azure/storage/blobs/storage-quickstart-blobs-storage-explorer)
                         
    * **Télécharger le chemin d’accès**: Vous pouvez indiquer l’emplacement de stockage pour l’envoi de ressources de projet Jar ou Scala. Il existe plusieurs types de stockage pris en charge : **Session interactive Spark permet de charger** et **WebHDFS usage à télécharger**
    
2. Cliquez sur **SparkJobRun** pour envoyer votre projet pour le cluster sélectionné. La progression de l’exécution de la tâche est affichée au bas de l’onglet **Remote Spark Job in Cluster** (Tâche Spark distante du cluster). Vous pouvez arrêter l’application en cliquant sur le bouton rouge.  

    ![cluster de Big Data Link - exécuter](./media/spark-submit-job-intellij-tool-plugin/link-ariscluster-run.png)

## <a name="spark-console"></a>Console Spark
Vous pouvez exécutez Spark Local Console(Scala) ou Spark Livy Interactive Session Console(Scala).

### <a name="spark-local-consolescala"></a>Spark Local Console(Scala)
Vérifiez que le prérequis relatif à WINUTILS.EXE est respecté.

1. À partir de la barre de menus, accédez à **Run** > **Edit Configurations...** (Exécuter > Modifier les configurations).

2. À partir de la **exécuter/déboguer des Configurations** fenêtre, dans le volet gauche, accédez à **Apache Spark sur un cluster de données volumineux de SQL Server** >  **[Spark sur SQL] myApp**.

3. Dans la fenêtre principale, sélectionnez l’onglet **Locally Run** (Exécuter localement).

4. Entrez les valeurs suivantes, puis sélectionnez **OK** :

    |Propriété |Valeur |
    |----|----|
    |Job main class (Classe main du travail)|la valeur par défaut est la classe main du fichier sélectionné. Vous pouvez modifier la classe en sélectionnant les points de suspension ( **...** ) pour choisir une autre classe.|
    |Variables d’environnement|Vérifiez que la valeur de HADOOP_HOME est correcte.|
    |WINUTILS.exe location (Emplacement de WINUTILS.exe)|Vérifiez que le chemin est correct.|

    ![Configuration de la console locale](./media/spark-submit-job-intellij-tool-plugin/console-set-configuration.png)

5. À partir de Project, accédez à **myApp** > **src** > **main** > **scala** > **myApp**.  

6. À partir de la barre de menus, accédez à **Tools** > **Spark Console** > **Run Spark Local Console(Scala)** (Outils > Console Spark > Exécuter la console Spark locale (Scala)).

7. Ensuite, deux boîtes de dialogue peuvent s’afficher pour vous demander si vous souhaitez corriger automatiquement les dépendances. Dans ce cas, sélectionnez **Auto Fix** (Correction automatique).

    ![Spark Auto Fix1](./media/spark-submit-job-intellij-tool-plugin/console-auto-fix1.png)

    ![Spark Auto Fix2](./media/spark-submit-job-intellij-tool-plugin/console-auto-fix2.png)

8. La console doit ressembler à l’image ci-dessous. Dans la fenêtre de console, tapez `sc.appName`, puis appuyez sur Ctrl+Entrée.  Le résultat s’affichera. Vous pouvez clore la console locale en cliquant sur le bouton rouge.

    ![Résultat dans la console locale](./media/spark-submit-job-intellij-tool-plugin/local-console-result.png)


### <a name="spark-livy-interactive-session-consolescala"></a>Spark Livy Interactive Session Console(Scala)
Le Console(Scala) de Session Interactive Spark Livy est uniquement pris en charge IntelliJ 2018.2 et 2018.3.

1. À partir de la barre de menus, accédez à **Run** > **Edit Configurations...** (Exécuter > Modifier les configurations).

2. À partir de la **exécuter/déboguer des Configurations** fenêtre, dans le volet gauche, accédez à **Apache Spark sur un cluster de données volumineux de SQL Server** >  **[Spark sur SQL] myApp**.

3. Dans la fenêtre principale, sélectionnez l’onglet **Remotely Run in Cluster** (Exécuter à distance dans le cluster).

4. Entrez les valeurs suivantes, puis sélectionnez **OK** :

    |Propriété |Valeur |
    |----|----|
    |Clusters Spark (Linux uniquement)|Sélectionnez le cluster Big Data de SQL Server sur lequel vous souhaitez exécuter votre application.|
    |Nom de la classe main|la valeur par défaut est la classe main du fichier sélectionné. Vous pouvez modifier la classe en sélectionnant les points de suspension ( **...** ) pour choisir une autre classe.|

    ![Configuration de la console interactive](./media/spark-submit-job-intellij-tool-plugin/interactive-console-configuration.png)

5. À partir de Project, accédez à **myApp** > **src** > **main** > **scala** > **myApp**.  

6. À partir de la barre de menus, accédez à **Tools** > **Spark Console** > **Run Spark Livy Interactive Session Console(Scala)** (Exécuter la console de session interactive Spark Livy (Scala)).

7. La console doit ressembler à l’image ci-dessous. Dans la fenêtre de console, tapez `sc.appName`, puis appuyez sur Ctrl+Entrée.  Le résultat s’affichera. Vous pouvez clore la console locale en cliquant sur le bouton rouge.

    ![Résultat dans la console interactive](./media/spark-submit-job-intellij-tool-plugin/interactive-console-result.png)

### <a name="send-selection-to-spark-console"></a>Envoyer la sélection à la Console de Spark

Pour plus de commodité, vous pouvez voir le résultat du script en envoyant du code à la Console locale ou Console(Scala) de Session Interactive Livy. Vous pouvez mettre en évidence du code dans le fichier Scala, puis cliquer avec le bouton droit sur **Send Selection To Spark Console** (Envoyer la sélection à la console Spark). Le code sélectionné est envoyé à la console afin d’être traité. Le résultat s’affiche après le code dans la console. La console vérifiera les erreurs s’il y en a.  

   ![Envoyer la sélection à la Console de Spark](./media/spark-submit-job-intellij-tool-plugin/send-selection-to-console.png)

## <a name="next-steps"></a>Étapes suivantes
Pour plus d’informations sur le cluster de données volumineux de SQL Server et les scénarios associés, consultez [que sont les clusters de données volumineuses de SQL Server 2019](big-data-cluster-overview.md)?
