---
title: Créer des rapports d’analyse dans l’Assistant expérimentation de base de données pour les mises à niveau de SQL Server
description: Créer des rapports d’analyse dans l’Assistant expérimentation de base de données
ms.custom: ''
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
manager: craigg
ms.openlocfilehash: 2d0e07e069754e961b290b33d77cb30b522c367f
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66015150"
---
# <a name="create-analysis-reports-in-database-experimentation-assistant"></a>Créer des rapports d’analyse dans l’Assistant expérimentation de base de données

Une fois que vous relisez la trace de la source sur les deux de vos serveurs cibles, vous pouvez générer un rapport d’analyse dans la base de données expérimentation Compagnon (DEA). Rapports d’analyse vous aider à obtenir des informations sur l’impact sur les performances des modifications proposées.

## <a name="create-an-analysis-report"></a>Créer un rapport d’analyse

Dans la DEA, sélectionnez l’icône de menu. Dans le menu développé, sélectionnez **rapports d’analyse** près de l’icône de liste de vérification.

![Menu d’analyse](./media/database-experimentation-assistant-create-report/dea-create-reports-menu.png)

Sous **rapports d’analyse**, sélectionnez **nouveau rapport d’analyse**.

![Nouveau menu de rapport d’analyse](./media/database-experimentation-assistant-create-report/dea-create-reports-new-report.png)

Entrez ou sélectionnez les informations suivantes :

- **Nom du rapport**: Entrez un nom pour votre rapport. Le nom du rapport est utilisé à la fois pour A et les bases de données B. Exemple : *A (ou B)* + *nom_élément_rapport* + *identificateur unique*. 
- **Nom du serveur** : Entrez le nom de l’ordinateur de serveur que vous souhaitez inclure dans A, B et les bases de données analysis.
- **Nom de l’instance SQL Server**: Entrez le nom de l’instance de SQL Server à utiliser pour le rapport.
- **Trace de serveur source**: Entrez le fichier de trace (.trc) première de SQL Server (2008 R2).
- **Trace de serveur cible**: Entrez la cible SQL Server (2014) premier fichier .trc.

![Nouvelle page de rapport d’analyse](./media/database-experimentation-assistant-create-report/dea-create-reports-inputs.png)

## <a name="generate-a-report"></a>Générer un rapport

Une fois que vous entrez ou sélectionnez les informations requises sur le **nouveau rapport d’analyse** page, sélectionnez **Démarrer** pour commencer à créer le rapport. Si les informations que vous avez entré sont valides, le rapport d’analyse est créé. Sinon, les zones de texte qui contiennent des informations non valides sont mises en surbrillance en rouge. Assurez-vous que vous entrez les valeurs correctes, puis sélectionnez **Démarrer**. 

Un rapport d’analyse est généré. La base de données analysis suit le schéma d’affectation de noms Analysis + *nom du rapport spécifié par l’utilisateur* + *identificateur unique*.

## <a name="frequently-asked-questions-about-analysis-reports"></a>Forum aux questions sur les rapports d’analyse

### <a name="what-does-my-analysis-report-tell-me"></a>Ce que mon rapport d’analyse indique ?
    
DEA utilise tests statistiques pour analyser votre charge de travail et déterminer comment chaque requête s’est exécutée à partir de la cible 1 à 2 de la cible. Il fournit des détails des performances pour chaque requête. En savoir plus sur la DEA dans [prise en main](database-experimentation-assistant-get-started.md).
    
### <a name="can-i-create-a-new-analysis-report-while-another-report-is-being-generated"></a>Puis-je créer un rapport d’analyse pendant la génération d’un autre rapport ?
    
Non.  Actuellement, un seul rapport peut être généré à la fois pour éviter les conflits. Toutefois, vous pouvez exécuter plus d’une capture et relire en même temps.

### <a name="i-upgraded-dea-to-version-20-can-i-still-view-and-use-my-old-reports"></a>La DEA mise à niveau vers la version 2.0. Puis-je toujours afficher et utiliser mes rapports ancien ?
    
Oui. Pour afficher les rapports générés précédemment, vous devez mettre à jour le schéma du rapport. Pour plus d’informations, consultez [DEA 2.0 : Schéma de base de données de mise à jour pour le rapport d’analyse dans DEA](https://blogs.msdn.microsoft.com/datamigration/2017/03/24/dea-2-0-updating-db-schema-for-analysis-report-in-the-database-experimentation-assistant/).
    
### <a name="can-i-generate-an-analysis-report-by-using-the-command-prompt"></a>Puis-je générer un rapport d’analyse à l’aide de l’invite de commandes ?
    
Oui. Vous pouvez générer un rapport d’analyse à l’invite de commandes. Vous pouvez ensuite afficher le rapport dans l’interface utilisateur. Pour plus d’informations, consultez [s’exécutent à l’invite de commandes](database-experimentation-assistant-run-command-prompt.md).
    
## <a name="troubleshoot-analysis-reports"></a>Résoudre les problèmes des rapports d’analyse

###  <a name="what-security-permissions-do-i-need-to-generate-and-view-an-analysis-report-on-my-server"></a>Les autorisations de sécurité dois-je générer et afficher un rapport d’analyse sur mon serveur ?
    
L’utilisateur qui est connecté à la DEA doit disposer des droits d’administrateur système sur le serveur d’analyse. Si l’utilisateur fait partie d’un groupe, assurez-vous que le groupe dispose des droits d’administrateur système.

|Erreurs possibles|Solution|  
|---|---|  
|Impossible de se connecter à la base de données. Vérifiez que vous disposez des droits d’administrateur système pour l’analyse et l’affichage des rapports.|Vous ne disposez pas des droits d’accès ou sysadmin sur le serveur ou la base de données. Vérifiez vos droits de connexion et réessayez.|  
|Impossible de générer **Nom_élément_rapport** sur le serveur **nom du serveur**. Pour plus d’informations, consultez le **Nom_élément_rapport** rapport.|Vous ne disposez pas des droits d’administrateur système nécessaires pour générer un nouveau rapport. Pour afficher les erreurs détaillées, sélectionnez le rapport erronées et vérifiez les journaux dans % temp%\\DEA.|  
|L’utilisateur actuel n’a pas les autorisations requises pour exécuter l’opération. Vérifiez que vous disposez des droits d’administrateur système pour effectuer le suivi et l’analyse des rapports.|Vous n’avez pas les droits d’administrateur système nécessaires pour générer un nouveau rapport.|  

### <a name="i-cant-connect-to-the-computer-running-sql-server"></a>Impossible de me connecter à l’ordinateur exécutant SQL Server
    
- Vérifiez que le nom de l’ordinateur exécutant SQL Server est valid. Pour vérifier, essayez de vous connecter au serveur à l’aide de SQL Server Management Studio (SSMS).
- Vérifiez que votre configuration de pare-feu ne bloque pas les connexions à l’ordinateur exécutant SQL Server.
- Vérifiez que l’utilisateur dispose des droits d’utilisateur nécessaires. 

Vous pouvez voir plus de détails dans les journaux dans % temp%\\DEA. Si le problème persiste, contactez l’équipe de produit.

### <a name="i-see-an-error-when-i-generate-an-analysis-report"></a>L’erreur s’affiche lorsque je génère un rapport d’analyse
    
Accès à Internet est nécessaire à la première fois que vous générez un rapport d’analyse après avoir installé la DEA. Accès à Internet est nécessaire pour télécharger les packages qui sont nécessaires pour l’analyse statistique.

Si une erreur se produit pendant que le rapport est créé, la page de progression indique l’échec de la génération de l’analyse une étape spécifique. Vous pouvez voir plus de détails dans les journaux dans % temp%\\DEA. Vérifiez que vous disposez d’une connexion valide au serveur avec les droits d’utilisateur requis, puis réessayez. Si le problème persiste, contactez l’équipe de produit.

|Erreurs possibles|Solution|  
|---|---|  
|RInterop a rencontré une erreur au démarrage. Vérifiez les journaux de RInterop et réessayez.|La DEA requiert un accès internet pour télécharger les packages R dépendants. Consultez RInterop journaux dans % temp%\\RInterop et DEA journaux dans % temp%\\DEA. Si RInterop a été initialisée correctement ou s’il est initialisé sans les packages R corrects, vous pouvez voir l’exception « Impossible de générer un nouveau rapport d’analyse » après l’étape InitializeRInterop dans les journaux DEA.<br><br>Les journaux RInterop également peuvent afficher une erreur semblable à « aucune jsonlite package n’est disponible. » Si votre ordinateur n’a pas accès à internet, vous pouvez télécharger manuellement le package requis jsonlite R :<br><br><li>Accédez à la variable % profil_utilisateur %\\dossier DEARPackages sur le système de fichiers de la machine. Ce dossier se compose de packages utilisés par R pour DEA.</li><br><li>Si le dossier jsonlite est manquant dans la liste des packages installés, vous avez besoin d’un ordinateur connecté à internet pour télécharger la version release de jsonlite\_1.4.zip de [ https://cran.r-project.org/web/packages/jsonlite/index.html ](https://cran.r-project.org/web/packages/jsonlite/index.html).</li><br><li>Copiez le fichier .zip sur l’ordinateur où vous exécutez DEA.  Extrayez le dossier jsonlite et copiez-le dans % UserProfile%\\DEARPackages. Cette étape installe automatiquement le package jsonlite dans R. Le dossier doit être nommé **jsonlite** et le contenu doit être directement dans le dossier, pas un niveau en dessous.</li><br><li>Fermez DEA, rouvrez et l’analyse d’essayez à nouveau.</li><br>Vous pouvez également utiliser l’interface RGUI. Accédez à **packages** > **installer à partir de zip**. Accédez au package que vous avez téléchargé précédemment et installez.<br><br>Si RInterop a été initialisé et configuré correctement, vous devez voir « Installation dépendants R jsonlite du package » dans les journaux RInterop.|  
|Impossible de se connecter à l’instance de SQL Server, assurez-vous que le nom du serveur est correct et recherchez l’accès requis pour l’utilisateur qui s’est connecté.|Vous ne disposez pas d’accès ou les droits d’utilisateur sur le serveur ou le nom du serveur est peut-être incorrects.| 
|Processus de RInterop a expiré. Examinez les journaux DEA et RInterop, arrêter le processus RInterop dans le Gestionnaire des tâches, puis recommencez l’opération.<br><br>ou Gestionnaire de configuration<br><br>RInterop est en état d’erreur. Arrêter le processus RInterop dans le Gestionnaire des tâches, puis recommencez l’opération.|Consultez les journaux dans % temp%\\RInterop pour confirmer l’erreur. Supprimer le processus RInterop Gestionnaire de tâches avant de réessayer. Contactez l’équipe de produit si le problème persiste.| 

### <a name="the-report-is-generated-but-data-appears-to-be-missing"></a>Le rapport est généré, mais les données semblent être manquant
    
Vérifiez la base de données sur l’ordinateur d’analyse qui exécute SQL Server pour confirmer qu’il existe des données. Vérifiez que la base de données d’analyse existe et vérifier ses tables. Par exemple, vérifier ces tables : TblBatchesA, TblBatchesB et TblSummaryStats.

Si les données n’existent pas, les données ne peuvent pas avoir copié correctement ou la base de données est peut-être endommagé. Si seules certaines données sont manquantes, les fichiers de trace créés dans la capture ou de votre charge de travail n’ont ne peut-être pas été capturée avec précision par relecture. Si les données, vérifiez les fichiers journaux dans % temp%\\DEA pour voir si des erreurs ont été consignées. Ensuite, réessayez de générer le rapport d’analyse.

Plusieurs questions ou des commentaires ? Envoyer des commentaires via l’outil DEA en sélectionnant l’icône de sourire dans l’angle inférieur gauche.  

## <a name="next-steps"></a>Étapes suivantes

- Pour savoir comment afficher le rapport d’analyse, consultez [afficher des rapports](database-experimentation-assistant-view-report.md).

- Pour une présentation 19 minutes DEA et de démonstration, regardez la vidéo suivante :

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
