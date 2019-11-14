---
title: Relire une trace pour les mises à niveau de SQL Server
description: Relire une trace avec Assistant Expérimentation de base de données pour les mises à niveau SQL Server
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
ms.openlocfilehash: b1607aefdc8495f374b2586b0b896f20e87f62d1
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056700"
---
# <a name="replay-a-trace-in-database-experimentation-assistant"></a>Relire une trace dans Assistant Expérimentation de base de données

Dans Assistant Expérimentation de base de données (DEA), vous pouvez relire un fichier de trace capturé sur un environnement de test mis à niveau. Par exemple, considérez une charge de travail de production qui s’exécute sur SQL Server 2008 R2. Le fichier de trace de la charge de travail doit être relu deux fois : une fois sur un environnement avec la même version de SQL Server qui s’exécute en production et de nouveau sur un environnement dont la version de la cible de mise à niveau SQL Server, par exemple SQL Server 2016.

> [!NOTE]
> Pour exécuter cette action, vous devez configurer manuellement des machines virtuelles ou des ordinateurs physiques pour exécuter Distributed Replay traces. Pour plus d’informations, consultez [configuration du contrôleur et des clients Distributed Replay](https://blogs.msdn.microsoft.com/datamigration/distributed-replay-controller-and-client-setup/).
>
>

## <a name="create-a-trace-replay"></a>Créer une relecture de trace

Dans DEA, sélectionnez l’icône de menu. Dans le menu développé, sélectionnez **relire les traces** en regard de l’icône de lecture.

![Sélectionner les traces de relecture dans le menu](./media/database-experimentation-assistant-replay-trace/dea-replay-trace-open.png)

> [!NOTE]
> L’ordinateur du contrôleur de Distributed Replay requiert des autorisations sur le compte d’utilisateur que vous utilisez pour l’accès à distance.
>

### <a name="grant-access-to-the-distributed-replay-controller"></a>Accorder l’accès au contrôleur Distributed Replay

1. À l’invite de commandes, entrez **DCOMCNFG** pour ouvrir l’interface **services de composants** .
1. Développez **services de composants** > **ordinateurs** > **poste de travail** > **DCOM Config** > **DReplayController**.
1. Cliquez avec le bouton droit sur **DReplayController**, puis sélectionnez **Propriétés**.
1. Sous l’onglet **sécurité** , sélectionnez **modifier** pour ajouter le compte d’utilisateur.
1. Sélectionnez **OK**.

### <a name="verify-setup"></a>Vérifier l’installation

1.  **SQL Server chemin d’installation**: entrez le chemin d’accès à l’emplacement d’installation de SQL Server. Par exemple, C :\\Program Files (x86)\\Microsoft SQL Server\\120.
1.  **Nom de l’ordinateur contrôleur**: entrez un nom pour l’ordinateur qui a été configuré en tant que contrôleur. Cet ordinateur exécute le service Windows nommé SQL Server contrôleur de Distributed Replay. Le contrôleur Distributed Replay orchestre les actions des clients Distributed Replay. Chaque environnement Distributed Replay ne doit contenir qu'une seule instance de contrôleur.
1.  **Noms des ordinateurs clients**: entrez un nom pour chaque ordinateur client, en les séparant par des virgules. Exemple : CLIENT1, client2. Vous pouvez avoir jusqu’à cinq contrôleurs clients. Les clients sont une ou plusieurs machines physiques ou virtuelles qui exécutent le service Windows nommé SQL Server client Distributed Replay. Les clients Distributed Replay fonctionnent ensemble pour simuler les charges de travail sur une instance de SQL Server. Chaque environnement Distributed Replay peut contenir un ou plusieurs clients.
1.  Sélectionnez **Suivant**.

### <a name="select-a-trace"></a>Sélectionner une trace

1.  **Chemin du fichier de trace**: entrez le chemin d’accès au fichier de trace d’entrée (. trc).
1.  **Chemin de la sortie du prétraitement de la relecture du magasin**:  
    \- si vous n’avez pas encore le fichier IRF, entrez le chemin d’accès à l’emplacement où vous souhaitez stocker le fichier IRF et les autres sorties de prétraitement.  
    \- si vous disposez déjà du fichier IRF, entrez le chemin d’accès aux fichiers IRF.
1. Sélectionnez **Suivant**.

### <a name="replay-a-trace"></a>Relire une trace

1.  **Nom du fichier de trace**: entrez un nom de fichier de trace.
1.  **Taille de fichier maximale (Mo)** : entrez la valeur de la taille de substitution du fichier de trace. La valeur par défaut est 200 Mo. Vous pouvez entrer une valeur personnalisée.
1.  **Chemin de la sortie de la trace de relecture du magasin**: entrez le chemin d’accès du fichier. trc de sortie.
1.  **SQL Server nom**de l’instance : entrez le nom de l’instance de SQL Server sur laquelle relire les traces.
1.  Sélectionnez **Démarrer**.

Si les informations que vous avez entrées sont valides, le processus de Distributed Replay démarre. Dans le cas contraire, les Boses de texte qui contiennent des informations incorrectes sont mises en surbrillance en rouge. Assurez-vous que les valeurs entrées sont correctes, puis sélectionnez **Démarrer**.

Attendez la fin de l’exécution de la relecture pour voir l’emplacement que vous avez spécifié. Sélectionnez l’icône représentant une cloche au bas du menu de gauche pour surveiller la progression de la relecture.

![Progression de la relecture des traces](./media/database-experimentation-assistant-replay-trace/dea-replay-trace-progress.png)

## <a name="frequently-asked-questions-about-trace-replay"></a>Forum aux questions sur la relecture de trace

### <a name="what-security-permissions-do-i-need-to-start-a-replay-capture-on-my-target-server"></a>Quelles sont les autorisations de sécurité nécessaires pour démarrer une capture de relecture sur mon serveur cible ?

- L’utilisateur Windows qui exécute l’opération de suivi dans l’application de DEA doit disposer de droits d’administrateur système sur l’ordinateur cible qui exécute SQL Server. Ces droits d’utilisateur sont nécessaires pour démarrer une trace.
- Le compte de service sous lequel l’ordinateur cible exécutant SQL Server s’exécute doit disposer d’un accès en écriture au chemin d’accès au fichier de trace spécifié.
- Le compte de service sous lequel s’exécutent les services du client Distributed Replay doit disposer de droits d’utilisateur pour se connecter à l’ordinateur cible exécutant SQL Server et pour exécuter des requêtes.

### <a name="can-i-start-more-than-one-replay-in-the-same-session"></a>Puis-je démarrer plusieurs relectures au cours d’une même session ?

Oui, vous pouvez démarrer plusieurs relectures et effectuer leur suivi jusqu’à la fin de la même session.

### <a name="can-i-start-more-than-one-replay-in-parallel"></a>Puis-je démarrer plusieurs relectures en parallèle ?

Oui, mais pas avec le même ensemble de machines sélectionnées dans le **contrôleur et les clients**. Le contrôleur et les clients seront occupés. Configurez un ensemble distinct de machines sous le **contrôleur et le client** pour démarrer une relecture parallèle.

### <a name="how-long-does-a-replay-typically-take-to-finish"></a>Combien de temps une relecture prend-elle généralement pour se terminer ?

Une relecture prend généralement le même temps que la trace source, plus la durée nécessaire pour prétraiter la trace source. Toutefois, si les ordinateurs clients inscrits auprès du contrôleur ne sont pas suffisants pour gérer la charge produite à partir de la relecture, la relecture peut prendre plus de temps. Vous pouvez inscrire jusqu’à 16 ordinateurs clients auprès du contrôleur.

### <a name="how-large-do-target-trace-files-get"></a>Quelle est la taille des fichiers de trace cibles ?

Les fichiers de trace cibles peuvent avoir une taille comprise entre 5 et 15 fois la taille de la trace source. La taille du fichier est basée sur le nombre de requêtes exécutées. Par exemple, les objets BLOB de plan de requête peuvent être volumineux. Si les statistiques de ces requêtes changent souvent, davantage d’événements sont capturés.

### <a name="why-do-i-need-to-restore-databases"></a>Pourquoi dois-je restaurer les bases de données ?

SQL Server est un système de gestion de base de données relationnelle avec état. Pour exécuter correctement un test A/B, l’état de la base de données doit être conservé à tout moment. Dans le cas contraire, vous risquez de voir des erreurs dans les requêtes pendant la relecture qui n’apparaîtront pas en production. Pour éviter ces erreurs, nous vous recommandons d’effectuer une sauvegarde juste avant la capture source. De même, la restauration de la sauvegarde sur l’ordinateur cible qui exécute SQL Server est nécessaire pour éviter les erreurs lors de la relecture.

### <a name="what-does-pass--on-the-replay-page-mean"></a>Que signifie « Pass% » sur la page de relecture ?

**Pass%** signifie que seul un pourcentage de requêtes a réussi. Vous pouvez diagnostiquer si le nombre d’erreurs est attendu. Les erreurs peuvent être attendues, ou les erreurs peuvent se produire parce que la base de données a perdu son intégrité. Si la valeur de la **passe%** n’est pas celle attendue, vous pouvez arrêter la trace et examiner le fichier de trace dans le générateur de profils SQL pour voir les requêtes qui n’ont pas réussi.

### <a name="how-can-i-look-at-the-trace-events-that-were-collected-during-replay"></a>Comment puis-je examiner les événements de trace qui ont été collectés lors de la relecture ?

Ouvrez un fichier de trace cible et affichez-le dans le générateur de profils SQL. Ou, si vous souhaitez apporter des modifications à la capture de relecture, tous les scripts SQL Server sont disponibles dans C :\\Program Files (x86)\\Microsoft Corporation\\Assistant Expérimentation de base de données\\scripts\\StartReplayCapture. Sql.

### <a name="what-trace-events-does-dea-collect-during-replay"></a>Quels sont les événements de trace collectés par DEA pendant la relecture ?

La DEA capture les événements de trace qui contiennent des informations relatives aux performances. La configuration de capture se trouve dans le script StartReplayCaptureTrace. Sql. Ces événements sont typiques SQL Server événements de trace répertoriés dans la [documentation de référence sp_trace_setevent (Transact-SQL)](https://docs.microsoft.com/sql/relational-databases/system-stored-procedures/sp-trace-setevent-transact-sql).

## <a name="troubleshoot-trace-replay"></a>Résoudre les problèmes de relecture de trace

### <a name="i-cant-connect-to-the-computer-thats-running-sql-server"></a>Je ne peux pas me connecter à l’ordinateur qui exécute SQL Server

- Confirmez que le nom de l’ordinateur exécutant SQL Server est valide. Pour confirmer, essayez de vous connecter au serveur à l’aide de SQL Server Management Studio (SSMS).
- Vérifiez que la configuration du pare-feu ne bloque pas les connexions à l’ordinateur exécutant SQL Server.
- Confirmez que l’utilisateur dispose des droits d’utilisateur requis.
- Vérifiez que le compte de service du client Distributed Replay a accès à l’ordinateur exécutant SQL Server.

Vous pouvez obtenir plus de détails dans les journaux de% temp%\\DEA. Si le problème persiste, contactez l’équipe du produit.

### <a name="i-cant-connect-to-the-distributed-replay-controller"></a>Je ne peux pas me connecter au contrôleur Distributed Replay

- Vérifiez que le service du contrôleur de Distributed Replay est en cours d’exécution sur l’ordinateur contrôleur. Pour vérifier, utilisez les outils d’administration Distributed Replay (exécutez la commande `dreplay.exe status -f 1`).
- Si la relecture est démarrée à distance :
  - Vérifiez que l’ordinateur qui exécute la DEA peut effectuer un test ping sur le contrôleur. Vérifiez que les paramètres du pare-feu autorisent les connexions en suivant les instructions de la page **configurer l’environnement de relecture** . Pour plus d’informations, consultez l’article [SQL Server Distributed Replay](https://docs.microsoft.com/sql/tools/distributed-replay/sql-server-distributed-replay?view=sql-server-2017).
  - Assurez-vous que le lancement à distance DCOM et l’activation à distance sont autorisés pour l’utilisateur du contrôleur de Distributed Replay.
  - Assurez-vous que les droits d’utilisateur de l’accès à distance DCOM sont autorisés pour l’utilisateur du contrôleur de Distributed Replay.

### <a name="the-trace-file-path-exists-on-my-machine-why-cant-distributed-replay-controller-find-it"></a>Le chemin d’accès au fichier de trace existe sur mon ordinateur. Pourquoi Distributed Replay contrôleur ne peut-il pas le Rechercher ?

Distributed Replay pouvez accéder uniquement aux ressources de disque local. Vous devez copier les fichiers de trace source sur l’ordinateur du contrôleur de Distributed Replay avant de démarrer la relecture. Vous devez également fournir le chemin d’accès sur la page **nouvelle relecture** de la DEA. 

Les chemins d’accès UNC ne sont pas compatibles avec Distributed Replay. Distributed Replay chemins d’accès doivent être des chemins d’accès locaux et absolus au premier fichier de trace source, y compris l’extension.

### <a name="why-cant-i-browse-for-files-on-the-new-replay-page"></a>Pourquoi ne puis-je pas Rechercher des fichiers sur la nouvelle page de relecture ?

Étant donné que nous ne pouvons pas parcourir les dossiers d’une machine distante, la recherche de fichiers n’est pas utile. La copie et le collage des chemins d’accès absolus sont plus efficaces.

### <a name="i-started-replay-with-a-trace-but-distributed-replay-didnt-replay-any-events"></a>J’ai commencé à relire avec une trace, mais Distributed Replay n’a pas relu les événements

Ce problème peut se produire si le fichier de trace n’a pas d’événements pouvant être relus ou s’il ne contient pas d’informations sur la façon de relire les événements. Vérifiez si le chemin d’accès au fichier de trace fourni est un fichier de trace source. Le fichier de trace source est créé à l’aide de la configuration fournie dans le script StartCaptureTrace. Sql.

### <a name="i-see-unexpected-error-occurred-when-i-try-to-preprocess-my-trace-files-by-using-the-sql-server-2017-distributed-replay-controller"></a>Je vois « une erreur inattendue s’est produite ». Lorsque j’essaie de prétraiter mes fichiers de trace à l’aide du contrôleur SQL Server 2017 Distributed Replay

Ce problème est connu dans la version RTM de SQL Server 2017. Pour plus d’informations, consultez [erreur inattendue lorsque vous utilisez la fonctionnalité DReplay pour relire une trace capturée dans SQL Server 2017](https://support.microsoft.com/help/4045678/fix-unexpected-error-when-you-use-the-dreplay-feature-to-replay-a).  
  
Le problème a été résolu dans la dernière mise à jour cumulative 1 pour SQL Server 2017. Téléchargez la dernière version de la [mise à jour cumulative 1 pour SQL Server 2017](https://support.microsoft.com/help/4038634/cumulative-update-1-for-sql-server-2017).

## <a name="next-steps"></a>Étapes suivantes

- Pour créer un rapport d’analyse qui vous aide à obtenir des informations sur les modifications proposées, consultez [créer des rapports](database-experimentation-assistant-create-report.md).

- Pour une présentation de la DEA et de la démonstration de 19 minutes, regardez la vidéo suivante :

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
