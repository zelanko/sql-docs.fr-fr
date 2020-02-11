---
title: Exécuter Assistant Expérimentation de base de données à partir d’une invite de commandes
description: Exécuter Assistant Expérimentation de base de données à partir d’une invite de commandes
ms.custom: seo-lt-2019
ms.date: 01/24/2020
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: jtoland
ms.reviewer: mathoma
ms.openlocfilehash: 8055ae8b66c2f2b59f18b0ee40dcac8753c0eb7c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "76831751"
---
# <a name="run-database-experimentation-assistant-at-a-command-prompt"></a>Exécuter Assistant Expérimentation de base de données à partir d’une invite de commandes

Cet article explique comment capturer une trace dans Assistant Expérimentation de base de données (DEA), puis analyser les résultats, le tout à partir d’une invite de commandes.

## <a name="start-a-new-workload-capture-by-using-the-dea-command"></a>Démarrer une nouvelle capture de la charge de travail à l’aide de la commande DEA

Pour démarrer une nouvelle capture de la charge de travail, à l’invite de commandes, exécutez la commande suivante :

`Deacmd.exe -o startcapturetrace -s <SQLServerInstance> -e <encryptconnection> -u <trustservercertificate> -d <database name> -p <trace file path> -f <trace file name> -t <Max duration>`

**Exemple**

`Deacmd.exe -o startcapturetrace -s localhost -e -d adventureworks -p c:\test -f sql2008capture -t 60`

## <a name="replay-a-workload-capture"></a>Relire une capture de la charge de travail

1. Connectez-vous à l’ordinateur du contrôleur de Distributed Replay.
2. Pour convertir la trace de charge de travail que vous avez capturée à l’aide de la commande de DEA dans un fichier IRF, à l’invite de commandes, exécutez la commande suivante :

    `DReplay preprocess -m "dreplaycontroller" -i "Path to first trace file" -d "<Folder path on controller>\IrfFolder"`

3. Démarrez une capture de trace sur l’ordinateur cible qui exécute SQL Server à l’aide de StartReplayCaptureTrace. Sql.

    a.  Dans SQL Server Management Studio (SSMS), ouvrez <Dea_InstallPath\>\Scripts\StartReplayCaptureTrace.Sql.

    b.  Exécutez `Set @durationInMins=0` afin que la capture de trace ne s’arrête pas automatiquement après une heure spécifiée.

    c.  Pour définir la taille de fichier maximale par fichier de trace `Set @maxfilesize`, exécutez. La taille recommandée est de 200 (en Mo).

    d.  Modifiez `@Tracefile` pour définir un nom unique pour votre fichier de trace.

    e.  Modifiez `@dbname` pour spécifier un nom de base de données si la charge de travail doit être capturée uniquement sur une base de données spécifique. Par défaut, la charge de travail sur l’ensemble du serveur est capturée.

4. Pour relire le fichier IRF sur l’instance de SQL Server cible, à l’invite de commandes, exécutez la commande suivante :

    `DReplay replay -m "dreplaycontroller" -d "<Folder Path on Dreplay Controller>\IrfFolder" -o -s "SQL2016Target" -w "dreplaychild1,dreplaychild2,dreplaycild3,dreplaychild4"`

    a.  Pour surveiller l’État, à l’invite de commandes, `DReplay status -f 1`exécutez.

    b.  Pour arrêter la relecture, par exemple si vous constatez que le% de réussite est inférieur à la valeur attendue, `DReplay cancel`à l’invite de commandes, exécutez.

5. Arrêtez la capture de trace sur l’instance de SQL Server cible.
6. Dans SSMS, ouvrez `<Dea_InstallPath>\Scripts\StopCaptureTrace.sql`.
7. Modifiez `@Tracefile` pour qu’il corresponde au chemin d’accès du fichier de trace sur l’ordinateur cible qui exécute SQL Server.
8. Exécutez le script sur l’ordinateur cible qui exécute SQL Server.

## <a name="analyze-traces-using-the-dea-command"></a>Analyser les traces à l’aide de la commande DEA

Pour démarrer une nouvelle analyse de trace, à l’invite de commandes, exécutez la commande suivante :

`Deacmd.exe -o analysis -a <Target1 trace filepath> -b <Target2 trace filepath> -r reportname -s <SQLserverInstance> -e <encryptconnection> -u <trustservercertificate>`

**Exemple**

`Deacmd.exe -o analysis -a C:\Trace\SQL2008Source\Trace.trc -b C:\ Trace\SQL2014Trace\Trace.trc -r upgrade20082014 -s localhost -e`

## <a name="see-also"></a>Voir aussi

- Pour plus d’informations sur l’utilisation de DEA, consultez [vue d’ensemble des Assistant expérimentation de base de données](database-experimentation-assistant-overview.md).
