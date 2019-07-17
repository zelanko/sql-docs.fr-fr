---
title: Résolution des problèmes d’un blocage ou d’un incident avec SQL Server Management Studio (SSMS)
ms.prod: sql
ms.prod_service: sql-tools
ms.reviewer: dnethi
ms.technology: ssms
ms.topic: conceptual
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: markingmyname
ms.author: maghan
manager: jroth
ms.custom: ''
ms.date: 07/01/2019
ms.openlocfilehash: 41f140a00669e1b5809b83b369f86ba8b277a37e
ms.sourcegitcommit: aeb2273d779930e76b3e907ec03397eab0866494
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67716769"
---
# <a name="get-diagnostic-data-after-a-sql-server-management-studio-ssms-crash"></a>Obtenir des données de diagnostic après un incident de SQL Server Management Studio (SSMS)

[!INCLUDE[S’applique à](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)

## <a name="get-full-memory-dump-after-a-hang-or-crash"></a>Obtenir l’image mémoire complète après un blocage ou un incident

Obtenez une image mémoire complète de SQL Server Management Studio (SSMS) lors d’un blocage ou d’un incident.

Pour capturer des informations de diagnostic pour détecter un problème de blocage ou d’incident du SSMS, suivez les étapes ci-dessous.

1. Télécharger [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx).

2. Décompressez le téléchargement dans un dossier.

3. Ouvrez une invite de commandes et exécutez la commande suivante.

    ```invite de commandes  <PathToProcDumpFolder>\procdump.exe -e -h -ma -w ssms.exe
    ```

    If it prompts you to accept a license agreement, select *Agree*.

4. Start SSMS, if it hasn't started already.

5. Reproduce the issue.

6. The text should appear in the cmd prompt about writing the dump file, wait for that to finish.

7. Create a new folder and copy the *.dmp file that is written out to that folder.

8. Copy the following files into the same folder.

    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll"
    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll"
    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll"

9. Zip up the folder

## Get full memory dump for an OutOfMemoryException

Get a full memory dump of SSMS when it throws an OutOfMemoryException.

You can get a full memory dump with any managed exception.

To capture diagnostic information to troubleshoot an OutOfMemoryException from SSMS, follow the steps below.

1. Download [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx).

2. Unzip the download into a folder.

3. Open Command Prompt and run the following command.

    ```command prompt
    <PathToProcDumpFolder>\procdump.exe -e 1 -f System.OutOfMemoryException -ma -w ssms.exe
    ```

    S’il vous invite à accepter un contrat de licence, sélectionnez *Accepter*.

4. Démarrez SSMS (SQL Server Management Studio) s’il n’est pas déjà démarré.

5. Reproduisez le problème.

6. Le texte doit apparaître dans l’invite de commandes sur l’écriture du fichier de sauvegarde, attendez la fin.

7. Créez un nouveau dossier et copiez le fichier *.dmp qui est écrit dans ce dossier.

8. Copiez les fichiers suivants dans le même dossier.

    "C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll"  "C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll"

9. Compresser le dossier.