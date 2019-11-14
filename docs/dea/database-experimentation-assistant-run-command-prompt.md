---
title: Exécuter Assistant Expérimentation de base de données à partir d’une invite de commandes
description: Exécuter Assistant Expérimentation de base de données à partir d’une invite de commandes
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
ms.openlocfilehash: c3b87eafa460cfef69666a3837f56626dab81d47
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056575"
---
# <a name="run-database-experimentation-assistant-at-a-command-prompt-sql-server"></a>Exécuter Assistant Expérimentation de base de données à partir d’une invite de commandes (SQL Server)

Cet article explique comment utiliser la fenêtre d’invite de commandes pour capturer une trace dans Assistant Expérimentation de base de données (DEA), puis analyser les résultats. 

## <a name="start-a-new-workload-capture-by-using-the-dea-command"></a>Démarrer une nouvelle capture de la charge de travail à l’aide de la commande DEA

Pour démarrer une nouvelle capture de la charge de travail, exécutez la commande suivante :

`Deacmd.exe -o startcapturetrace -s <SQLServerInstance> -e <encryptconnection> -u <trustservercertificate> -d <database name> -p <trace file path> -f <trace file name> -t <Max duration>`

**Exemple**

`Deacmd.exe -o startcapturetrace -s localhost -e -d adventureworks -p c:\test -f sql2008capture -t 60`

## <a name="replay-a-workload"></a>Relire une charge de travail

1.  Connectez-vous à l’ordinateur du contrôleur de Distributed Replay.
2.  Convertissez la trace de charge de travail que vous avez capturée à l’aide de la commande de DEA dans un fichier IRF :

    `DReplay preprocess -m "dreplaycontroller" -i "Path to first trace file" -d "<Folder path on controller>\IrfFolder"`

3.  Démarrez une capture de trace sur l’ordinateur cible qui exécute SQL Server à l’aide de StartReplayCaptureTrace. Sql.
       
    a.  Dans SQL Server Management Studio (SSMS), ouvrez < Dea_InstallPath\>\Scripts\StartReplayCaptureTrace.sql.
    
    b.  Exécutez `Set @durationInMins=0` afin que la capture de trace ne s’arrête pas automatiquement après une heure spécifiée.
    
    c.  Pour définir la taille de fichier maximale par fichier de trace, exécutez `Set @maxfilesize`. La taille recommandée est de 200 (en Mo).
    
    d.  Modifiez `@Tracefile` pour définir un nom unique pour votre fichier de trace.
    
    e.  Modifiez `@dbname` pour spécifier un nom de base de données si la charge de travail doit être capturée uniquement sur une base de données spécifique. Par défaut, la charge de travail sur l’ensemble du serveur est capturée. 
4.  Relire le fichier IRF sur l’instance de SQL Server cible :

    `DReplay replay -m "dreplaycontroller" -d "<Folder Path on Dreplay Controller>\IrfFolder" -o -s "SQL2016Target" -w "dreplaychild1,dreplaychild2,dreplaycild3,dreplaychild4"`
        
    a.  Pour surveiller l’État, ouvrez une fenêtre d’invite de commandes et exécutez `DReplay status -f 1`.
        
    b.  Pour arrêter la relecture, par exemple si vous voyez que le% de réussite est inférieur à la valeur attendue, ouvrez une fenêtre d’invite de commandes et exécutez `DReplay cancel`.

5.  Arrêtez la capture de trace sur l’instance de SQL Server cible.
6.  Dans SSMS, ouvrez `<Dea_InstallPath>\Scripts\StopCaptureTrace.sql`.
7.  Modifiez `@Tracefile` pour qu’il corresponde au chemin d’accès du fichier de trace sur l’ordinateur cible qui exécute SQL Server.
8.  Exécutez le script sur l’ordinateur cible qui exécute SQL Server.

## <a name="analyze-traces-by-using-the-dea-command"></a>Analyser les traces à l’aide de la commande DEA

Pour démarrer une nouvelle analyse de trace, exécutez la commande suivante :

`Deacmd.exe -o analysis -a <Target1 trace filepath> -b <Target2 trace filepath> -r reportname -s <SQLserverInstance> -e <encryptconnection> -u <trustservercertificate>`

**Exemple**

`Deacmd.exe -o analysis -a C:\Trace\SQL2008Source\Trace.trc -b C:\ Trace\SQL2014Trace\Trace.trc -r upgrade20082014 -s localhost -e`

## <a name="next-steps"></a>Étapes suivantes

Pour une présentation de la DEA et de la démonstration de 19 minutes, regardez la vidéo suivante :

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
