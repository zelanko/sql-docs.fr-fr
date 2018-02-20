---
title: Notes de publication | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b8459ed8-625e-4d8b-891c-e7e78c9977cc
caps.latest.revision: 
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.openlocfilehash: 44c73c4d632fd434fcd296dc6fc2cc70af26086c
ms.sourcegitcommit: 4edac878b4751efa57601fe263c6b787b391bc7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/19/2018
---
# <a name="release-notes"></a>Notes de publication
[!INCLUDE[Driver_ODBC_Download](../../../includes/driver_odbc_download.md)]

  Notes de publication pour Microsoft ODBC Driver for SQL Server sur Windows.  

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-17-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Quelles sont les nouveautés le [!INCLUDE[msCoName](../../../includes/msconame_md.md)] le pilote ODBC 17 pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sur Windows

**Fonctionnalités ajoutées**:

Always Encrypted prise en charge des API BCP

Nouvel attribut de chaîne de connexion UseFMTOnly conduit le pilote à utiliser les métadonnées héritées dans les cas spéciaux exigeant des tables temporaires.

Prise en charge pour l’Instance gérée de SQL Azure (version préliminaire privée étendu). 
> [!NOTE]
> Il existe plusieurs différences lors de l’utilisation d’une Instance gérée :
> -   FILESTREAM n’est pas pris en charge. 
> -   Accès de système de fichiers local n’est pas pris en charge, mais nécessaires pour les opérations que tracefiles 
> -   Créer des UDT local chemin d’accès n’est pas pris en charge. 
> -   L’authentification Windows intégrée n’est pas pris en charge. 
> -   DTC n’est pas pris en charge. 
> -   compte 'sa' n’est pas présent (compte par défaut est appelé « cloudSA »)
> -   Erreur de jeton TDS (0xAA) renvoie le nom de serveur incorrect
> -   Caractères spéciaux dans le nom de la base de données ne sont pas pris en charge. 
> -   MODIFIER le nom de ALTER DATABASE [dbname1] = [dbname2] n’est pas pris en charge.
> -   Les messages d’erreur sont toujours affichées en anglais, quel que soit le langage de paramètres (identique à Azure) 
  
## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-131-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Quelles sont les nouveautés le [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13.1 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sur Windows  
 ODBC Driver 13.1 pour [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] ajoute la prise en charge de [Always Encrypted](../../../connect/odbc/using-always-encrypted-with-the-odbc-driver.md) et [Azure Active Directory](../../../connect/odbc/using-azure-active-directory.md) lorsqu’il est utilisé conjointement avec Microsoft SQL Server 2016.  Connexion de mise en pool des mots clés et attributs sont décrits dans [pilote prenant en charge le regroupement de connexions dans le pilote ODBC pour SQL Server](../../../connect/odbc/windows/driver-aware-connection-pooling-in-the-odbc-driver-for-sql-server.md).

 ## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-13-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Quelles sont les nouveautés le [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 13 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sur Windows  
 ODBC Driver 13 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] inclut une fonctionnalité précédente à partir d’ODBC Driver 11 pour SQL Server et ajoute la prise en charge de Microsoft SQL Server 2016.

## <a name="whats-new-in-the-includemsconameincludesmsconamemdmd-odbc-driver-11-for-includessnoversionincludesssnoversionmdmd-on-windows"></a>Quelles sont les nouveautés le [!INCLUDE[msCoName](../../../includes/msconame_md.md)] ODBC Driver 11 for [!INCLUDE[ssNoVersion](../../../includes/ssnoversion_md.md)] sur Windows  
 ODBC Driver 11 pour SQL Server contient de nouveaux [fonctionnalités](./features-of-the-microsoft-odbc-driver-for-sql-server-on-windows.md) , ainsi que toutes les fonctionnalités fournies avec ODBC dans SQL Server 2012 Native Client.  
