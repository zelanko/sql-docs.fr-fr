---
title: Exécutez l’Assistant expérimentation de base de données à une invite de commandes pour les mises à niveau de SQL Server
description: Exécutez l’Assistant expérimentation de base de données à une invite de commandes
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
ms.openlocfilehash: 475c3dc1366e69dbc164547bbf5dfc8c06515c56
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68050468"
---
# <a name="run-database-experimentation-assistant-at-a-command-prompt"></a>Exécutez l’Assistant expérimentation de base de données à une invite de commandes

Cet article décrit comment utiliser la fenêtre d’invite de commande pour capturer une trace dans la base de données expérimentation Compagnon (DEA) et ensuite analyser les résultats. 

## <a name="start-a-new-workload-capture-by-using-the-dea-command"></a>Démarrer une nouvelle charge de travail de capture à l’aide de la commande DEA

Pour démarrer une nouvelle capture de la charge de travail, exécutez la commande suivante :

`Deacmd.exe -o startcapturetrace -s <SQLServerInstance> -e <encryptconnection> -u <trustservercertificate> -d <database name> -p <trace file path> -f <trace file name> -t <Max duration>`

**Exemple**

`Deacmd.exe -o startcapturetrace -s localhost -e -d adventureworks -p c:\test -f sql2008capture -t 60`

## <a name="replay-a-workload"></a>Relire une charge de travail

1.  Connectez-vous à l’ordinateur du contrôleur Distributed Replay.
2.  Convertir la trace de charge de travail que vous avez capturés à l’aide de la commande DEA vers un fichier HAPLOTYPES IRF :

    `DReplay preprocess -m "dreplaycontroller" -i "Path to first trace file" -d "<Folder path on controller>\IrfFolder"`

3.  Démarrer une capture de trace sur l’ordinateur cible en cours d’exécution SQL Server à l’aide de StartReplayCaptureTrace.sql.
       
    a.  Dans SQL Server Management Studio (SSMS), ouvrez < Dea_InstallPath\>\Scripts\StartReplayCaptureTrace.sql.
    
    b.  Exécutez `Set @durationInMins=0` afin que la capture de trace ne s’arrête pas automatiquement après un délai spécifié.
    
    c.  Pour définir la taille de fichier maximale par fichier de trace, exécutez `Set @maxfilesize`. La taille recommandée est de 200 (en Mo).
    
    d.  Modifier `@Tracefile` pour définir un nom unique pour votre fichier de trace.
    
    e.  Modifier `@dbname` pour spécifier un nom de base de données si la charge de travail doit être capturée uniquement sur une base de données spécifique. Par défaut, la charge de travail sur l’ensemble du serveur est capturée. 
4.  Relire le fichier HAPLOTYPES IRF par rapport à l’instance de SQL Server cible :

    `DReplay replay -m "dreplaycontroller" -d "<Folder Path on Dreplay Controller>\IrfFolder" -o -s "SQL2016Target" -w "dreplaychild1,dreplaychild2,dreplaycild3,dreplaychild4"`
        
    a.  Pour surveiller l’état, ouvrez une fenêtre d’invite de commandes et exécutez `DReplay status -f 1`.
        
    b.  Pour arrêter la relecture, telles que si vous voyez que le pourcentage de réussite est plus faible que prévu, ouvrez une fenêtre d’invite de commandes et exécutez `DReplay cancel`.

5.  Arrêtez la capture de trace sur l’instance de SQL Server cible.
6.  Dans SSMS, ouvrez `<Dea_InstallPath>\Scripts\StopCaptureTrace.sql`.
7.  Modifier `@Tracefile` pour faire correspondre le chemin d’accès du fichier de trace sur l’ordinateur cible qui exécute SQL Server.
8.  Exécutez le script sur l’ordinateur cible qui exécute SQL Server.

## <a name="analyze-traces-by-using-the-dea-command"></a>Analyser des traces à l’aide de la commande DEA

Pour démarrer une nouvelle analyse de trace, exécutez la commande suivante :

`Deacmd.exe -o analysis -a <Target1 trace filepath> -b <Target2 trace filepath> -r reportname -s <SQLserverInstance> -e <encryptconnection> -u <trustservercertificate>`

**Exemple**

`Deacmd.exe -o analysis -a C:\Trace\SQL2008Source\Trace.trc -b C:\ Trace\SQL2014Trace\Trace.trc -r upgrade20082014 -s localhost -e`

## <a name="next-steps"></a>Étapes suivantes

Pour une présentation 19 minutes DEA et de démonstration, regardez la vidéo suivante :

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]
