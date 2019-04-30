---
title: Exécuter un fichier de script Reporting Services | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- scripts [Reporting Services], running
ms.assetid: 0de4995c-85ec-4d4c-aaef-fbd30edfb20f
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 8d4023d5fb434f58fd031e6512f3fa84fa551fec
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63200975"
---
# <a name="run-a-reporting-services-script-file"></a>Exécuter un fichier de script Reporting Services
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Les fichiers de script sont exécutés à partir de l’invite de commandes à l’aide de l’environnement de script [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] (RS.exe). RS.exe possède de nombreux arguments d'invite de commandes que vous pouvez utiliser. Pour plus d’informations sur les options d’invite de commandes, consultez [Utilitaire RS.exe &#40;SSRS&#41;](rs-exe-utility-ssrs.md). Pour d’autres exemples de scripts, consultez [Exemples de produit SQL Server Reporting Services](https://go.microsoft.com/fwlink/?LinkId=177889).  
  
## <a name="sample-command-lines"></a>Exemples de lignes de commande  
  
-   Exécutez Script.rss dans l'environnement de script qui désigne le serveur de rapports cible. L'authentification Windows est appliquée par défaut :  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver  
    ```  
  
-   Exécutez Script.rss dans l'environnement de script en spécifiant un nom d'utilisateur et un mot de passe pour authentifier les appels de service Web :  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -u myusername -p mypassword  
    ```  
  
-   Exécutez Script.rss dans l'environnement de script en spécifiant un délai d'expiration de serveur égal à 30 secondes :  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -l 30  
    ```  
  
-   Exécutez Script.rss dans l’environnement de script en spécifiant une variable de script globale appelée *report*.  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -v report="Company Sales"  
    ```  
  
-   Exécutez Script.rss dans l'environnement de script en spécifiant que les opérations de service Web du fichier de script s'exécutent en tant que lot.  
  
    ```  
    rs -i Script.rss -s http://servername/reportserver -b  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Informations techniques de référence &#40;SSRS&#41;](../technical-reference-ssrs.md)  
  
  
