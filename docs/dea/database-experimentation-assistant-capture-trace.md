---
title: Capturer une trace pour les mises à niveau de SQL Server
description: Capturer une trace dans Assistant Expérimentation de base de données pour les mises à niveau SQL Server
ms.custom: seo-lt-2019
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
ms.openlocfilehash: 6c24632875d09125efcd043ae907e87a21847fe9
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056602"
---
# <a name="capture-a-trace-in-database-experimentation-assistant"></a>Capturer une trace dans Assistant Expérimentation de base de données

Vous pouvez utiliser une capture de trace dans Assistant Expérimentation de base de données (DEA) pour créer un fichier de trace qui contient un journal des événements de serveur capturés. Un événement de serveur capturé est un événement qui se produit sur un serveur spécifique pendant une période de temps spécifique. Une capture de trace doit être exécutée une fois par serveur.

Avant de démarrer une capture de trace, assurez-vous de sauvegarder toutes les bases de données cibles.

La mise en cache des requêtes dans SQL Server peut affecter les résultats de l’évaluation. Nous vous recommandons de redémarrer le service de SQL Server (MSSQLSERVER) dans l’application des services pour améliorer la cohérence des résultats de l’évaluation.

## <a name="create-a-trace-capture"></a>Créer une capture de trace

1. Dans DEA, sélectionnez l’icône de menu dans le menu de gauche. Dans le menu développé, sélectionnez **capturer les traces** en regard de l’icône de l’appareil photo.

    ![Sélectionnez capturer les traces dans le menu](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-capture.png)

1. Sous **nouvelle capture**, entrez ou sélectionnez les informations suivantes :

    - **SQL Server nom**de l’instance : entrez un nom pour l’ordinateur exécutant SQL Server sur lequel vous souhaitez capturer une trace de serveur.
    - **Nom de la base de données**: entrez le nom d’une base de données sur laquelle démarrer une trace de base de données. Si vous ne spécifiez pas de base de données, la trace est capturée sur toutes les bases de données sur le serveur.
    - **Nom du fichier de trace**: entrez un nom pour le fichier de trace de votre capture.
    - **Taille de fichier maximale (Mo)** : sélectionnez la taille de substitution des fichiers. Un nouveau fichier est créé si nécessaire, à la taille de fichier que vous sélectionnez. La taille de substitution recommandée est de 200 Mo.
    - **Durée (min)** : sélectionnez la durée (en minutes) pendant laquelle vous souhaitez que la capture de trace s’exécute.
    - **Chemin de stockage du fichier de trace de sortie**: sélectionnez le chemin de destination du fichier de trace. 

    > [!NOTE]
    > Le chemin d’accès au fichier de trace doit se trouver sur l’ordinateur qui exécute SQL Server. Si le service SQL Server n’est pas défini pour un compte spécifique, le service peut avoir besoin d’autorisations en écriture sur le dossier spécifié pour le fichier de trace à écrire.
    >
    >

    ![Nouvelle page de capture](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-inputs.png)

## <a name="start-the-trace-capture"></a>Démarrer la capture de trace

Une fois que vous avez entré ou sélectionné les informations requises, sélectionnez **Démarrer** pour démarrer la capture des traces. Si les informations que vous avez entrées sont valides, le processus de capture de trace commence. Sinon, les zones de texte qui comportent des entrées non valides sont mises en surbrillance en rouge. 

Assurez-vous que les valeurs que vous avez sélectionnées ou entrées sont correctes, puis sélectionnez **Démarrer**.

Une fois l’exécution de la capture de trace terminée, localisez votre nouveau fichier de trace à l’emplacement de fichier que vous avez spécifié dans **chemin d’accès au stockage du fichier de trace de sortie**. Sélectionnez l’icône représentant une cloche au bas du menu de gauche pour surveiller la progression de la capture.

![Progression de la capture des traces](./media/database-experimentation-assistant-capture-trace/dea-capture-trace-progress.png)

### <a name="trace-file"></a>Fichier de suivi

La capture de trace écrit un fichier. trc à l’emplacement spécifié. Le fichier de trace comprend les résultats de trace de l’activité d’une base de données SQL Server. Les fichiers TRC sont conçus pour fournir plus d’informations sur les erreurs détectées et signalées par SQL Server.

## <a name="frequently-asked-questions-about-trace-capture"></a>Forum aux questions sur la capture de trace

Voici quelques questions fréquemment posées sur la capture de trace dans la DEA.

### <a name="what-events-are-captured-when-i-run-a-trace-capture-on-a-production-database"></a>Quels sont les événements capturés lors de l’exécution d’une capture de trace sur une base de données de production ?

Le tableau suivant fournit la liste des événements et les données de colonnes correspondantes que nous recueillons pour les traces :
  
|Nom d'événement|Données texte (1)|Données binaires (2)|ID de base de données (3)|Nom d’hôte (8)|Nom de l’application (10)|Nom de connexion (11)|SPID (12)|Heure de début (14)|Heure de fin (15)|Nom de la base de données (35)|Séquence d’événements (51)|IsSystem (60)|  
|---|---|---|---|---|---|---|---|---|---|---|---|---|  
|**RPC : terminé (10)**||*|*|*|*|*|*|*|*|*|*|*|  
|**RPC:Starting (11)**||*|*|*|*|*|*|*||*|*|*|  
|**Paramètre de sortie RPC (100)**|*||*|*|*|*|*|*||*|*|*|  
|**SQL:BatchCompleted (12)**|*||*|*|*|*|*|*|*|*|*|*|  
|**SQL:BatchStarting (13)**|*||*|*|*|*|*|*||*|*|*|  
|**Auditer la connexion (14)**|*|*|*|*|*|*|*|*||*|*|*|  
|**Audit de déconnexion (15)**|*||*|*|*|*|*|*|*|*|*|*|  
|**ExistingConnection (17)**|*|*|*|*|*|*|*|*||*|*|*|  
|**CursorOpen (53)**|*||*|*|*|*|*|*||*|*|*|  
|**CursorPrepare (70)**|*||*|*|*|*|*|*||*|*|*|  
|**Préparer SQL (71)**|||*|*|*|*|*|*||*|*|*|  
|**Exec Prepared SQL (72)**|||*|*|*|*|*|*||*|*|*|  
|**CursorExecute (74)**|*||*|*|*|*|*|*||*|*|*|  
|**CursorUnprepare (77)**|*||*|*|*|*|*|*||*|*|*|  
|**CursorClose (78)**|*||*|*|*|*|*|*||*|*|*|  

### <a name="is-there-a-performance-effect-on-my-production-server-when-trace-capture-is-running"></a>Y a-t-il un effet sur les performances sur mon serveur de production lorsque la capture de trace est en cours d’exécution ?
    
Oui, il y a un impact minime sur les performances lors de la collecte des traces. Dans nos tests, nous avons constaté une sollicitation de mémoire de 3%.
    
### <a name="what-kind-of-permissions-are-required-for-capturing-traces-on-a-production-workload"></a>Quels sont les types d’autorisations nécessaires pour capturer des suivis sur une charge de travail de production ?
    
- L’utilisateur Windows qui exécute l’opération de suivi dans l’application de DEA doit disposer de droits d’administrateur système sur l’ordinateur qui exécute SQL Server.
- Le compte de service utilisé sur l’ordinateur exécutant SQL Server doit avoir un accès en écriture au chemin d’accès au fichier de trace spécifié.

### <a name="can-i-capture-traces-for-the-entire-server-or-only-on-a-single-database"></a>Puis-je capturer des traces pour l’ensemble du serveur ou uniquement sur une base de données unique ?
    
Vous pouvez utiliser la DEA pour capturer les traces de toutes les bases de données du serveur ou d’une base de données unique.
    
### <a name="i-have-a-linked-server-configured-in-my-production-environment-do-those-queries-show-up-in-the-traces"></a>Je dispose d’un serveur lié configuré dans mon environnement de production. Ces requêtes apparaissent-elles dans les traces ?
    
Si vous exécutez une capture de trace pour l’ensemble du serveur, la trace capture toutes les requêtes, y compris les requêtes de serveur lié. Pour exécuter une capture de trace pour l’ensemble du serveur, laissez la zone **nom de la base de données** vide sous **nouvelle capture** vide.
    
### <a name="whats-the-minimum-recommended-time-for-production-workload-traces"></a>Quelle est la durée minimale recommandée pour les traces de charge de travail de production ?
    
Nous vous recommandons de choisir une heure qui représente le mieux l’intégralité de votre charge de travail. De cette façon, l’analyse s’exécute sur toutes les requêtes dans votre charge de travail.
    
### <a name="how-important-is-to-take-a-database-backup-right-before-i-start-a-trace-capture"></a>Quelle est la procédure à suivre pour effectuer une sauvegarde de base de données juste avant de démarrer une capture de trace ?
    
Avant de démarrer une capture de trace, assurez-vous de sauvegarder toutes vos bases de données cibles. La trace capturée dans cible 1 et cible 2 est relue. Si l’état de la base de données n’est pas le même, les résultats de l’expérimentation sont faussés.

### <a name="can-i-collect-xevents-instead-of-traces-and-can-i-replay-xevents"></a>Puis-je collecter des XEvents au lieu de traces, puis-je relire XEvents ?
    
Oui. La DEA prend en charge XEvents. Téléchargez la dernière version de DEA et essayez-la.

## <a name="troubleshoot-trace-captures"></a>Résoudre les problèmes de captures de trace

Si vous voyez une erreur lors de l’exécution d’une capture de trace, passez en revue les conditions préalables suivantes :

- Confirmez que le nom de l’ordinateur exécutant SQL Server est valide. Pour confirmer, essayez de vous connecter à l’ordinateur qui exécute SQL Server à l’aide de SQL Server Management Studio (SSMS).
- Vérifiez que la configuration de votre pare-feu ne bloque pas les connexions à l’ordinateur exécutant SQL Server.
- Vérifiez que l’utilisateur dispose des autorisations répertoriées dans le [Forum aux questions sur la relecture](https://blogs.msdn.microsoft.com/datamigration/2017/03/24/dea-2-0-replay-faq/)du blog.
- Confirmez que le nom de la trace ne respecte pas la Convention de substitution standard (capture\_1). Essayez plutôt des noms de trace comme capture\_1A ou Capture1.

Voici quelques-unes des erreurs possibles et des solutions pour les résoudre :

|Erreurs possibles|Solution|  
|---|---|  
|Impossible de démarrer la trace sur le SQL Server cible, de vérifier si vous disposez des autorisations requises et que le compte SQL Server dispose d’un accès en écriture au chemin d’accès du fichier de trace spécifié code d’erreur SQL (53)|L’utilisateur exécutant l’outil DEA doit avoir accès à l’ordinateur exécutant SQL Server. Le rôle sysadmin doit être attribué à l’utilisateur.|  
|Impossible de démarrer la trace sur le SQL Server cible, de vérifier si vous disposez des autorisations requises et que le compte SQL Server dispose d’un accès en écriture au chemin d’accès du fichier de trace spécifié code d’erreur SQL (19062)|Le chemin d’accès de suivi spécifié n’existe peut-être pas ou le dossier ne dispose pas des autorisations d’écriture pour le compte sous lequel les services SQL Server sont en cours d’exécution (par exemple, SERVICE réseau). Le chemin d’accès doit exister et doit avoir les autorisations nécessaires pour démarrer le suivi.|  
|Une trace de DEA est actuellement en cours d’exécution sur le serveur cible.|Une trace active est déjà en cours d’exécution sur le serveur cible. Vous ne pouvez pas démarrer une nouvelle trace lorsqu’une trace au niveau du serveur est déjà en cours d’exécution.|  
|Impossible d’ouvrir la base de données demandée pour la capture de la trace. Cette erreur peut être due à un nom de base de données incorrect.|La base de données spécifiée n’existe pas ou n’est pas accessible à l’utilisateur actuel. Utilisez le nom correct de la base de données.|  

Si vous voyez d’autres erreurs libellées *code d’erreur SQL*, consultez [moteur de base de données des erreurs](https://docs.microsoft.com/sql/relational-databases/errors-events/database-engine-events-and-errors) pour obtenir des descriptions détaillées.

## <a name="next-steps"></a>Étapes suivantes

- Pour savoir comment configurer les outils de Distributed Replay dans SQL Server avant de relire une trace capturée, consultez [configurer la relecture](database-experimentation-assistant-configure-replay.md).

- Pour une présentation de la DEA et de la démonstration de 19 minutes, regardez la vidéo suivante :

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
