---
title: Capturer une trace dans l’Assistant expérimentation de base de données pour les mises à niveau de SQL Server
description: Capturer une trace dans l’Assistant expérimentation de base de données
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
ms.reviewer: douglasl
manager: craigg
ms.openlocfilehash: a616686649ae6c373d3537d397fe56d709f08712
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "56987805"
---
# <a name="capture-a-trace-in-database-experimentation-assistant"></a>Capturer une trace dans l’Assistant expérimentation de base de données

Vous pouvez utiliser une capture de trace dans la base de données expérimentation Compagnon (DEA) pour créer un fichier de trace qui a un journal des événements de serveur capturés. Un événement de serveur capturés est un événement qui se produit sur un serveur spécifique pendant une période spécifique. Une capture de trace doit être exécutée une fois par serveur.

Avant de démarrer une capture de trace, veillez à sauvegarder toutes les bases de données cible.

Mise en cache de requête dans SQL Server peut affecter les résultats de l’évaluation. Nous recommandons que vous redémarrez le service SQL Server (MSSQLSERVER) dans l’application de services pour améliorer la cohérence des résultats d’évaluation.

## <a name="create-a-trace-capture"></a>Créer une capture de trace

1. Dans la DEA, sélectionnez l’icône de menu dans le menu de gauche. Dans le menu développé, sélectionnez **capturer des Traces** près de l’icône de l’appareil photo.

    ![Sélectionnez capturer des Traces dans le menu](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-capture.png)

1. Sous **nouvelle Capture**, entrez ou sélectionnez les informations suivantes :

    - **Nom de l’instance SQL Server**: Entrez un nom pour l’ordinateur exécutant SQL Server sur lequel vous souhaitez capturer une trace de serveur.
    - **Nom de la base de données**: Entrez un nom pour une base de données sur laquelle démarrer une trace de la base de données. Si vous ne spécifiez pas une base de données, la trace est capturée sur toutes les bases de données sur le serveur.
    - **Nom de fichier de trace**: Entrez un nom pour le fichier de trace pour votre capture.
    - **Taille de fichier maximale (Mo)**: Sélectionnez la taille de la substitution de fichiers. Un nouveau fichier est créé en fonction des besoins à la taille de fichier que vous sélectionnez. La taille recommandée de substitution est de 200 Mo.
    - **Durée (en mn)**: Sélectionnez la durée (en minutes) que vous souhaitez la capture de trace s’exécute.
    - **Chemin d’accès pour stocker le fichier de sortie de**: Sélectionnez le chemin d’accès de destination pour le fichier de trace. 

    > [!NOTE]
    > Le chemin d’accès de fichier pour le fichier de trace doit être sur l’ordinateur qui exécute SQL Server. Si le service SQL Server n’est pas défini pour un compte spécifique, le service peut devez autorisations en écriture sur le dossier spécifié pour le fichier de trace à écrire.
    >
    >

    ![Nouvelle page de Capture](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-inputs.png)

## <a name="start-the-trace-capture"></a>Démarrez la capture de trace

Une fois que vous entrez ou sélectionnez les informations requises, sélectionnez **Démarrer** pour démarrer la capture de traces. Si les informations que vous avez entré sont valides, le processus de capture de trace commence. Sinon, les zones de texte qui ont des entrées non valides sont mises en surbrillance en rouge. 

Assurez-vous que les valeurs que vous avez sélectionné ou entré sont corrects, puis sélectionnez **Démarrer**.

Lorsque la capture de trace est terminée en cours d’exécution, recherchez votre nouveau fichier de trace dans l’emplacement du fichier que vous avez spécifié dans **chemin d’accès pour stocker le fichier de sortie**. Sélectionnez l’icône représentant une cloche en bas du menu de gauche pour surveiller la progression de la capture.

![Capturer la progression de Traces](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-progress.png)

### <a name="trace-file"></a>Fichier de suivi

La capture de trace écrit un fichier .trc dans l’emplacement spécifié. Le fichier de trace inclut les résultats de trace de l’activité d’une base de données SQL Server. Fichiers TRC sont conçus pour fournir plus d’informations sur les erreurs qui sont détectées et signalées par SQL Server.

## <a name="frequently-asked-questions-about-trace-capture"></a>Questions fréquemment posées sur la capture de trace

Suivantes sont certaines questions fréquentes sur la capture de trace dans la DEA.

### <a name="what-events-are-captured-when-i-run-a-trace-capture-on-a-production-database"></a>Les événements qui sont capturées lorsque j’exécute une capture de trace sur une base de données de production ?

Le tableau suivant fournit la liste des événements et les données de colonne correspondantes que nous collectons des traces :
  
|Nom d'événement|Données de texte (1)|Données binaires (2)|ID de base de données (3)|Nom d’hôte (8)|Nom de l’application (10)|Nom de connexion (11)|SPID (12)|Heure de début (14)|Heure de fin (15)|Nom de la base de données (35)|Séquence d’événements (51)|IsSystem (60)|  
|---|---|---|---|---|---|---|---|---|---|---|---|---|  
|**RPC : terminé (10)**||*|*|*|*|*|*|*|*|*|*|*|  
|**RPC:Starting (11)**||*|*|*|*|*|*|*||*|*|*|  
|**RPC Output Parameter (100)**|*||*|*|*|*|*|*||*|*|*|  
|**SQL:BatchCompleted (12)**|*||*|*|*|*|*|*|*|*|*|*|  
|**SQL:BatchStarting (13)**|*||*|*|*|*|*|*||*|*|*|  
|**Audit Login (14)**|*|*|*|*|*|*|*|*||*|*|*|  
|**Audit Logout (15)**|*||*|*|*|*|*|*|*|*|*|*|  
|**ExistingConnection (17)**|*|*|*|*|*|*|*|*||*|*|*|  
|**CursorOpen (53)**|*||*|*|*|*|*|*||*|*|*|  
|**CursorPrepare (70)**|*||*|*|*|*|*|*||*|*|*|  
|**Prepare SQL (71)**|||*|*|*|*|*|*||*|*|*|  
|**Exec Prepared SQL (72)**|||*|*|*|*|*|*||*|*|*|  
|**CursorExecute (74)**|*||*|*|*|*|*|*||*|*|*|  
|**CursorUnprepare (77)**|*||*|*|*|*|*|*||*|*|*|  
|**CursorClose (78)**|*||*|*|*|*|*|*||*|*|*|  

### <a name="is-there-a-performance-effect-on-my-production-server-when-trace-capture-is-running"></a>Y a-t-il un impact sur mon serveur de production les performances lors de la capture de trace est en cours d’exécution ?
    
Oui, il existe un effet minimal sur les performances pendant la collecte de trace. Dans nos tests, nous avons trouvé sur une pression de mémoire de 3 %.
    
### <a name="what-kind-of-permissions-are-required-for-capturing-traces-on-a-production-workload"></a>Quels types d’autorisations sont nécessaires pour capturer des traces sur une charge de travail de production ?
    
- L’utilisateur de Windows qui exécute l’opération de trace dans l’application DEA doit disposer des droits d’administrateur système sur l’ordinateur qui exécute SQL Server.
- Le compte de service utilisé sur l’ordinateur exécutant SQL Server doit avoir accès en écriture pour le chemin d’accès du fichier de trace spécifié.

### <a name="can-i-capture-traces-for-the-entire-server-or-only-on-a-single-database"></a>Puis-je capturer des suivis pour l’ensemble du serveur ou uniquement sur une base de données unique ?
    
Vous pouvez utiliser la DEA pour capturer des traces pour toutes les bases de données sur le serveur ou pour une base de données.
    
### <a name="i-have-a-linked-server-configured-in-my-production-environment-do-those-queries-show-up-in-the-traces"></a>J’ai un serveur lié est configuré dans mon environnement de production. Ces requêtes apparaissent dans les traces ?
    
Si vous exécutez une capture de trace pour l’ensemble du serveur, la trace capture toutes les requêtes, y compris les requêtes de serveur lié. Pour exécuter une capture de trace pour l’ensemble du serveur, laissez le **nom de la base de données** sous **nouvelle Capture** vide.
    
### <a name="whats-the-minimum-recommended-time-for-production-workload-traces"></a>Qu’est l’heure minimale recommandée pour les traces de la charge de travail de production ?
    
Nous vous recommandons de choisir une heure qui correspond le mieux à l’intégralité de votre charge de travail. De cette façon, l’analyse s’exécute sur toutes les requêtes dans votre charge de travail.
    
### <a name="how-important-is-to-take-a-database-backup-right-before-i-start-a-trace-capture"></a>L’est important d’effectuer une sauvegarde de base de données approprié avant de commencer une capture de trace ?
    
Avant de démarrer une capture de trace, veillez à sauvegarder toutes vos bases de données cible. Relecture de la trace capturée dans la cible 1 et 2 de la cible. Si l’état de la base de données n’est pas le même, les résultats de l’expérimentation sont bloquées.

### <a name="can-i-collect-xevents-instead-of-traces-and-can-i-replay-xevents"></a>Collecte des événements étendus au lieu de traces et puis-je relire les événements étendus ?
    
Oui. La DEA prend en charge les événements étendus. Téléchargez la dernière version de DEA et faites un essai.

## <a name="troubleshoot-trace-captures"></a>Résoudre les problèmes de capture de trace

Si vous voyez une erreur lorsque vous exécutez une capture de trace, passez en revue les conditions préalables suivantes :

- Vérifiez que le nom de l’ordinateur exécutant SQL Server est valid. Pour vérifier, essayez de vous connecter à l’ordinateur exécutant SQL Server à l’aide de SQL Server Management Studio (SSMS).
- Vérifiez que votre configuration de pare-feu ne bloque pas les connexions à l’ordinateur exécutant SQL Server.
- Vérifiez que l’utilisateur dispose des autorisations qui sont répertoriées dans la publication de blog [FAQ de relecture](https://blogs.msdn.microsoft.com/datamigration/2017/03/24/dea-2-0-replay-faq/).
- Vérifiez que le nom de la trace ne suit pas la convention de substitution standard (capturer\_1). Au lieu de cela, essayez les noms de trace comme Capture\_1 a ou Capture1.

Voici certaines erreurs possibles, que vous pouvez voir et solutions pour les résoudre :

|Erreurs possibles|Solution|  
|---|---|  
|Impossible de démarrer la trace sur la cible de SQL Server, vérifiez si vous avez les autorisations requises et que le compte SQL Server a accès en écriture pour le chemin d’accès du fichier de trace spécifié le Code d’erreur Sql (53)|L’utilisateur qui exécute l’outil DEA doit avoir accès à l’ordinateur exécutant SQL Server. L’utilisateur doit avoir le rôle sysadmin.|  
|Impossible de démarrer la trace sur la cible de SQL Server, vérifiez si vous avez les autorisations requises et que le compte SQL Server a accès en écriture pour le chemin d’accès du fichier de trace spécifié le Code d’erreur Sql (19062)|Le chemin d’accès de trace spécifié n’existe ne peut-être pas ou le dossier n’a pas les autorisations d’écriture pour le compte sous lequel SQL Server services sont en cours d’exécution (par exemple, SERVICE réseau). Le chemin d’accès doit exister, et il doit avoir les autorisations requises pour la trace Démarrer.|  
|Une trace DEA actuellement est en cours d’exécution sur le serveur cible.|Une trace active est déjà en cours d’exécution sur le serveur cible. Impossible de démarrer une nouvelle trace lorsqu’une trace de l’échelle du serveur est déjà en cours d’exécution.|  
|Impossible d’ouvrir la base de données demandé pour la capture de trace. Cette erreur peut résulter d’un nom de base de données incorrect.|La base de données spécifié n’existe pas ou n’est pas accessible à l’utilisateur actuel. Utilisez le nom de la base de données correcte.|  

Si vous voyez les autres erreurs étiquetés *Code d’erreur Sql*, consultez [messages d’erreur système](https://docs.microsoft.com/previous-versions/sql/sql-server-2008-r2/cc645603(v=sql.105)) pour une description détaillée et des résolutions.
    
## <a name="next-steps"></a>Étapes suivantes

- Pour savoir comment configurer les outils de Distributed Replay dans SQL Server avant de vous relisez une trace capturée, consultez [configurer relecture](database-experimentation-assistant-configure-replay.md).

- Pour une présentation 19 minutes DEA et de démonstration, regardez la vidéo suivante :

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
