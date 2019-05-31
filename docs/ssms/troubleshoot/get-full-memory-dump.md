---
title: Obtenir une image mémoire complète pour résoudre les problèmes de SQL Server Management Studio (SSMS)
Description: Résolution des problèmes d’un blocage ou incident SSMS en collectant une image mémoire complète
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: how-to
ms.assetid: c28ffa44-7b8b-4efa-b755-c7a3b1c11ce4
author: markingmyname
ms.author: maghan
manager: craigg
ms.reviewer: dineth, sstein
ms.custom: ''
ms.date: 05/17/2019
ms.openlocfilehash: 2fbd0f4680c7a63a5390d93589f44b708f6c2629
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65983126"
---
# <a name="get-full-memory-dump"></a>Obtenir l’image mémoire complète

[!INCLUDE[Applies to](../../includes/appliesto-ss-asdb-asdw-xxx-md.md)]

Dans cet article, vous allez apprendre à capturer des informations de diagnostic pour résoudre un incident ou un blocage rencontré à partir de SQL Server Management Studio (SSMS).

Pour capturer des informations de diagnostic pour résoudre les problèmes, suivez les étapes ci-dessous.

1. Télécharger [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx).

2. Décompressez le téléchargement dans un dossier.

3. Ouvrez une invite de commandes et exécutez la commande suivante.

    ```cmd
    <PathToProcDumpFolder>\procdump.exe -e -h -ma -w ssms.exe
    ```

    Il vous invite à accepter un contrat de licence, sélectionnez **Accepter**.

4. Démarrez SSMS (SQL Server Management Studio) s’il n’est pas déjà démarré.

5. Reproduisez votre problème.

6. Le texte doit apparaître dans l’invite de commandes sur l’écriture du fichier de sauvegarde, attendez la fin.

7. Créez un nouveau dossier et copiez le fichier *.dmp qui est écrit dans ce dossier.

8. Copiez les fichiers suivants dans le même dossier.

    * « C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll »
    * « C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll »
    * « C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll »

9. Compresser le dossier.

## <a name="outofmemoryexception"></a>OutOfMemoryException

Vous pouvez également obtenir l’image mémoire complète de SSMS lorsqu’elle lève une exception OutOfMemoryException (n’importe quelle exception gérée).

Pour capturer des informations de diagnostic pour résoudre une OutOfMemoryException à partir du SSMS, suivez les étapes ci-dessous.

1. Télécharger [ProcDump](https://technet.microsoft.com/sysinternals/dd996900.aspx).

2. Décompressez le téléchargement dans un dossier.

3. Ouvrez une invite de commandes et exécutez la commande suivante.

    ```cmd
    <PathToProcDumpFolder>\procdump.exe -e 1 -f System.OutOfMemoryException -ma -w ssms.exe
    ```

    Il vous invite à accepter un contrat de licence, sélectionnez **Accepter**.

4. Démarrez SSMS (SQL Server Management Studio) s’il n’est pas déjà démarré.

5. Reproduisez le problème.

6. Le texte doit apparaître dans l’invite de commandes sur l’écriture du fichier de sauvegarde, attendez la fin.

7. Créez un nouveau dossier et copiez le fichier *.dmp qui est écrit dans ce dossier.

8. Copiez les fichiers suivants dans le même dossier.

    * « C:\Windows\Microsoft.NET\Framework\v4.0.30319\mscordacwks.dll »
    * « C:\Windows\Microsoft.NET\Framework\v4.0.30319\SOS.dll »
    * « C:\Windows\Microsoft.NET\Framework\v4.0.30319\clr.dll »

9. Compresser le dossier.

## <a name="share-the-information"></a>Partager les informations

1. Pour partager les informations avec l’équipe de SSMS, signalez le problème sur https://aka.ms/sqlfeedback.

2. Ensuite, partagez le fichier de vidage de la mémoire collecté sur OneDrive (ou équivalent) à un endroit où le fichier peut être collecté.

    > [!Important]
    > Les fichiers de vidage de la mémoire peuvent contenir des informations sensibles.

## <a name="next-steps"></a>Étapes suivantes

[SQL Server Management Studio](../sql-server-management-studio-ssms.md)