---
title: Relire une trace avec l’Assistant expérimentation de base de données pour les mises à niveau de SQL Server
description: Relire une trace avec l’Assistant expérimentation de base de données
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
manager: jroth
ms.openlocfilehash: 7db0e6a83997a3be7b204f780f3c0a7ad856b0d8
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794451"
---
# <a name="replay-a-trace-in-database-experimentation-assistant"></a>Relire une trace dans l’Assistant expérimentation de base de données

Dans base de données expérimentation Compagnon DEA (), vous pouvez relire un fichier de trace capturée sur un environnement de test mis à niveau. Par exemple, considérez une charge de travail de production qui s’exécute sur SQL Server 2008 R2. Le fichier de trace pour la charge de travail doit être relu à deux reprises : une fois dans un environnement avec la même version de SQL Server qui s’exécute sur la production et à nouveau sur un environnement qui comporte la version de SQL Server cible mise à niveau, tels que SQL Server 2016.

> [!NOTE]
> Pour exécuter cette action, vous devez définir manuellement des machines physiques ou des machines virtuelles pour exécuter des traces de Distributed Replay. Pour plus d’informations, consultez [le programme d’installation de contrôleur et les clients Distributed Replay](https://blogs.msdn.microsoft.com/datamigration/distributed-replay-controller-and-client-setup/).
>
>

## <a name="create-a-trace-replay"></a>Créer une relecture de trace

Dans la DEA, sélectionnez l’icône de menu. Dans le menu développé, sélectionnez **relire des Traces** en regard de l’icône de lecture.

![Dans le menu, sélectionnez relire des Traces](./media/database-experimentation-assistant-replay-trace/dea-replay-trace-open.png)

> [!NOTE]
> L’ordinateur du contrôleur Distributed Replay nécessite des autorisations au compte d’utilisateur que vous utilisez à distance.
>

### <a name="grant-access-to-the-distributed-replay-controller"></a>Accorder l’accès au contrôleur de Distributed Replay

1. À l’invite de commandes, entrez **dcomcnfg** pour ouvrir le **Services de composants** interface.
1. Développez **Services de composants** > **ordinateurs** > **mon ordinateur** > **configuration DCOM**  >  **DReplayController**.
1. Avec le bouton droit **DReplayController**, puis sélectionnez **propriétés**.
1. Sur le **sécurité** onglet, sélectionnez **modifier** pour ajouter le compte d’utilisateur.
1. Sélectionnez **OK**.

### <a name="verify-setup"></a>Vérifiez que le programme d’installation

1.  **Chemin d’installation de SQL Server**: Entrez le chemin d’accès où est installé SQL Server. Par exemple, C:\\Program Files (x86)\\Microsoft SQL Server\\120.
1.  **Nom de l’ordinateur contrôleur**: Entrez un nom pour l’ordinateur qui a été configuré en tant que le contrôleur. Cet ordinateur est en cours d’exécution du service Windows nommé SQL Server Distributed Replay controller. Le contrôleur de Distributed Replay orchestre les actions des clients Distributed Replay. Chaque environnement Distributed Replay ne doit contenir qu'une seule instance de contrôleur.
1.  **Noms d’ordinateur client**: Entrez un nom pour chaque ordinateur client, séparé par des virgules. Exemple : client1, client2. Vous pouvez avoir jusqu'à cinq contrôleurs de client. Les clients se trouvent un ou plusieurs ordinateurs, physiques ou virtuels, qui exécutent le service Windows nommé SQL Server Distributed Replay client. Les clients Distributed Replay fonctionnent ensemble pour simuler les charges de travail sur une instance de SQL Server. Chaque environnement Distributed Replay peut contenir un ou plusieurs clients.
1.  Sélectionnez **Suivant**.

### <a name="select-a-trace"></a>Sélectionnez un suivi

1.  **Chemin d’accès au fichier de trace**: Entrez le chemin d’accès du fichier de trace d’entrée (.trc).
1.  **Chemin d’accès pour stocker la relecture de prétraitement sortie**:  
    \- Si vous n’avez pas déjà le fichier HAPLOTYPES IRF, entrez le chemin d’accès à l’emplacement où vous souhaitez stocker le fichier HAPLOTYPES IRF et autres prétraitement génère.  
    \- Si vous avez déjà le fichier HAPLOTYPES IRF, entrez le chemin d’accès aux fichiers HAPLOTYPES IRF.
1. Sélectionnez **Suivant**.

### <a name="replay-a-trace"></a>Relire une trace

1.  **Nom de fichier de trace**: Entrez un nom de fichier de trace.
1.  **Taille de fichier maximale (Mo)** : Entrez une valeur de taille de la substitution de fichier trace. La valeur par défaut est de 200 Mo. Vous pouvez entrer une valeur personnalisée.
1.  **Chemin d’accès pour stocker la sortie de trace de relecture**: Entrez le chemin d’accès du fichier de sortie .trc.
1.  **Nom de l’instance SQL Server**:  Entrez le nom de l’instance de SQL Server sur lequel relire les traces.
1.  Sélectionnez **Démarrer**.

Si les informations que vous avez entré sont valides, le processus de Distributed Replay démarre. Sinon, les boses de texte qui contiennent des informations incorrectes sont mises en surbrillance en rouge. Assurez-vous que les valeurs saisies sont correctes, puis sélectionnez **Démarrer**.

Patientez jusqu'à la fin de la relecture en cours d’exécution pour afficher l’emplacement que vous avez spécifié. Sélectionnez l’icône représentant une cloche en bas du menu de gauche pour surveiller la progression de la relecture.

![Progression des Traces de relecture](./media/database-experimentation-assistant-replay-trace/dea-replay-trace-progress.png)

## <a name="frequently-asked-questions-about-trace-replay"></a>Questions fréquemment posées sur la relecture de trace

### <a name="what-security-permissions-do-i-need-to-start-a-replay-capture-on-my-target-server"></a>Les autorisations de sécurité que je dois démarrer une capture de relecture sur mon serveur cible

- L’utilisateur de Windows qui exécute l’opération de trace dans l’application DEA doit disposer des droits d’administrateur système sur l’ordinateur cible qui exécute SQL Server. Ces droits d’utilisateur sont nécessaires pour démarrer une trace.
- Le compte de service sous lequel l’ordinateur cible en cours d’exécution SQL Server s’exécute doit avoir accès en écriture pour le chemin d’accès du fichier de trace spécifié.
- Le compte de service sous lequel les services Distributed Replay Client sont en cours d’exécution doit disposer des droits d’utilisateur pour se connecter à l’ordinateur cible qui exécute SQL Server et d’exécuter des requêtes.

### <a name="can-i-start-more-than-one-replay-in-the-same-session"></a>Puis-je démarrer plusieurs relecture dans la même session ?

Oui, vous pouvez démarrer plusieurs relectures et assurer leur suivi jusqu'à la fin de la même session.

### <a name="can-i-start-more-than-one-replay-in-parallel"></a>Puis-je démarrer une plusieurs relecture en parallèle ?

Oui, mais pas avec le même ensemble de machines sélectionnées dans **contrôleur ainsi que les Clients**. Le contrôleur et les clients sera occupés. Configurer un ensemble distinct de machines sous **contrôleur plus Client** pour démarrer une relecture parallèle.

### <a name="how-long-does-a-replay-typically-take-to-finish"></a>La durée pendant laquelle une relecture généralement faut-il pour terminer ?

Une relecture prend généralement la même quantité de temps que la trace de la source ainsi que la quantité de temps que nécessaire pour la trace de la source de prétraitement. Toutefois, si les ordinateurs clients qui sont inscrits auprès du contrôleur ne sont pas suffisantes pour gérer la charge qui est générée à partir de la relecture, la relecture peut prendre plue de temps. Vous pouvez inscrire jusqu'à 16 ordinateurs clients avec le contrôleur.

### <a name="how-large-do-target-trace-files-get"></a>La taille des fichiers de trace cible est obtiens ?

La trace de la cible fichiers peuvent être compris entre 5 et 15 fois la taille de la trace de la source. La taille du fichier est basée sur le nombre de requêtes est exécuté. Par exemple, les objets BLOB de plan de requête peut être volumineuse. Si les statistiques pour ces requêtes changent souvent, plusieurs événements sont capturés.

### <a name="why-do-i-need-to-restore-databases"></a>Pourquoi je dois restaurer des bases de données ?

SQL Server est un système de gestion de base de données relationnelle avec état. Pour s’exécuter correctement un A / test B, l’état de la base de données doit être conservée en permanence. Sinon, vous pouvez rencontrer des erreurs dans les requêtes pendant la relecture n’apparaître pas dans la production. Pour éviter ces erreurs, nous vous recommandons une sauvegarde juste avant la capture de la source. De même, la restauration de la sauvegarde sur l’ordinateur cible qui exécute SQL Server est requise afin d’éviter des erreurs lors de la relecture.

### <a name="what-does-pass--on-the-replay-page-mean"></a>Ce que « passe % » sur la moyenne de page de relecture ?

**Passer %** signifie que seulement un pourcentage de requêtes est passé. Vous pouvez diagnostiquer si le nombre d’erreurs est attendu. Les erreurs susceptibles de contenir, ou les erreurs peuvent se produire, car la base de données a perdu son intégrité. Si la valeur de **pass %** n’est pas ce que vous attendiez, vous pouvez arrêter la trace et examinez le fichier de trace de Profiler de SQL pour voir les requêtes qui a échoué.

### <a name="how-can-i-look-at-the-trace-events-that-were-collected-during-replay"></a>Comment puis-je examiner les événements de trace qui ont été collectés pendant la relecture ?

Ouvrir un fichier de trace de cible et l’afficher dans SQL Profiler. Ou, si vous souhaitez apporter des modifications à la capture de relecture, tous les scripts SQL Server sont disponibles sur C:\\Program Files (x86)\\Microsoft Corporation\\Assistant expérimentation de base de données\\Scripts\\ StartReplayCapture.sql.

### <a name="what-trace-events-does-dea-collect-during-replay"></a>Les événements de trace collecte DEA pendant la relecture ?

La DEA capture les événements de trace qui contiennent des informations liées aux performances. La configuration de capture est dans le script StartReplayCaptureTrace.sql. Ces événements sont les événements de trace SQL Server standard qui sont répertoriées dans le [documentation de référence sp_trace_setevent (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql).

## <a name="troubleshoot-trace-replay"></a>Résoudre les problèmes de la relecture de trace

### <a name="i-cant-connect-to-the-computer-thats-running-sql-server"></a>Je ne parviens pas à se connecter à l’ordinateur qui exécute SQL Server

- Vérifiez que le nom de l’ordinateur exécutant SQL Server est valid. Pour vérifier, essayez de vous connecter au serveur à l’aide de SQL Server Management Studio (SSMS).
- Vérifiez que la configuration du pare-feu ne bloque pas les connexions à l’ordinateur exécutant SQL Server.
- Vérifiez que l’utilisateur dispose des droits d’utilisateur nécessaires.
- Vérifiez que le compte de service du client Distributed Replay a accès à l’ordinateur exécutant SQL Server.

Vous pouvez obtenir plus de détails dans les journaux dans % temp%\\DEA. Si le problème persiste, contactez l’équipe de produit.

### <a name="i-cant-connect-to-the-distributed-replay-controller"></a>Impossible de me connecter au contrôleur de Distributed Replay

- Vérifiez que le service Distributed Replay controller est en cours d’exécution sur l’ordinateur du contrôleur. Pour vérifier, utilisez les outils d’administration Distributed Replay (exécutez la commande `dreplay.exe status -f 1`).
- Si la relecture est démarrée à distance :
  - Vérifiez que l’ordinateur qui exécute la DEA peut communiquer correctement le contrôleur. Vérifiez que les paramètres de pare-feu autorisent les connexions selon les instructions sur la **configurer l’environnement de relecture** page. Pour plus d’informations, consultez l’article [SQL Server Distributed Replay](https://docs.microsoft.com/sql/tools/distributed-replay/sql-server-distributed-replay?view=sql-server-2017).
  - Assurez-vous que l’exécution à distance DCOM et Activation à distance sont autorisées pour l’utilisateur de Distributed Replay controller.
  - Assurez-vous que les droits d’accès à distance DCOM utilisateur sont autorisées pour l’utilisateur de Distributed Replay controller.

### <a name="the-trace-file-path-exists-on-my-machine-why-cant-distributed-replay-controller-find-it"></a>Le chemin d’accès du fichier de trace existe sur mon ordinateur. Pourquoi le contrôleur Distributed Replay ne peut pas trouver ?

Distributed Replay peut accéder uniquement les ressources de disque local. Vous devez copier les fichiers de trace source à la machine contrôleur Distributed Replay avant de démarrer la relecture. En outre, vous devez fournir le chemin d’accès sur la DEA **reprise** page. 

Chemins d’accès UNC ne sont pas compatibles avec Distributed Replay. Chemins d’accès de relecture distribuées doivent être des chemins d’accès locales, absolus pour le premier fichier de trace source, y compris d’extension.

### <a name="why-cant-i-browse-for-files-on-the-new-replay-page"></a>Pourquoi ne puis-je pas rechercher des fichiers dans la page nouvelle relecture ?

Étant donné que nous ne pouvons pas parcourir les dossiers d’un ordinateur distant, parcourez les fichiers n’est pas utile. Copier et coller les chemins d’accès absolus est plus efficace.

### <a name="i-started-replay-with-a-trace-but-distributed-replay-didnt-replay-any-events"></a>J’ai commencé la relecture avec une trace mais Distributed Replay n’a pas relire les événements

Ce problème peut se produire, car le fichier de trace n’avoir événements pouvant être relus ou il n’a pas d’informations sur la manière de relire les événements. Vérifiez si le chemin d’accès du fichier de trace fourni est un fichier de trace source. Le fichier de trace source est créé à l’aide de la configuration fournie dans le script StartCaptureTrace.sql.

### <a name="i-see-unexpected-error-occurred-when-i-try-to-preprocess-my-trace-files-by-using-the-sql-server-2017-distributed-replay-controller"></a>Je vois « une erreur inattendue s’est produite » ! Lorsque j’essaie de prétraitement mes fichiers de trace à l’aide de SQL Server 2017 Distributed Replay controller

Ce problème est connu dans la version RTM de SQL Server 2017. Pour plus d’informations, consultez [une erreur inattendue lorsque vous utilisez la fonctionnalité de DReplay pour relire une trace capturée dans SQL Server 2017](https://support.microsoft.com/help/4045678/fix-unexpected-error-when-you-use-the-dreplay-feature-to-replay-a).  
  
Le problème a été résolu dans la dernière à jour Cumulative 1 pour SQL Server 2017. Téléchargez la dernière version de [à jour Cumulative 1 pour SQL Server 2017](https://support.microsoft.com/help/4038634/cumulative-update-1-for-sql-server-2017).

## <a name="next-steps"></a>Étapes suivantes

- Pour créer un rapport d’analyse qui vous permet d’obtenir des informations sur les modifications proposées, consultez [créer des rapports](database-experimentation-assistant-create-report.md).

- Pour une présentation 19 minutes DEA et de démonstration, regardez la vidéo suivante :

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
