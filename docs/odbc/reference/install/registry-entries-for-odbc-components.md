---
title: Les entrées de Registre pour les composants ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC]
- installing ODBC components [ODBC], registry entries
- registry entries for components [ODBC]
- subkeys [ODBC], for components
- registry entries for components [ODBC], about registry entries
ms.assetid: c90aa8a4-6ece-48de-901c-17d23739a9ff
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3d0a654b70fb93020bbb0dcfde159b4884cb15c0
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63280973"
---
# <a name="registry-entries-for-odbc-components"></a>Entrées de Registre pour les composants ODBC
> [!NOTE]  
>  ODBC à partir de Windows XP et Windows Server 2003, est inclus dans le système d’exploitation Windows. Vous devez explicitement uniquement installer ODBC dans les versions antérieures de Windows.  
  
 Le programme d’installation DLL conserve les informations dans le Registre sur chaque composant ODBC installé. Sur les ordinateurs exécutant Microsoft Windows NT et Microsoft Windows 95/98, ces informations sont stockées dans les sous-clés sous la clé suivante dans le Registre :  
  
 HKEY_LOCAL_MACHINE  
  
 LOGICIEL  
  
 ODBC  
  
 Odbcinst.ini  
  
 Fichier Odbcinst.ini étant une sous-clé de l’arborescence HKEY_LOCAL_MACHINE, les informations sur les composants ODBC sont disponibles pour tous les utilisateurs de l’ordinateur.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Sous-clé des composants principaux ODBC](../../../odbc/reference/install/odbc-core-subkey.md)  
  
-   [Sous-clé des pilotes ODBC](../../../odbc/reference/install/odbc-drivers-subkey.md)  
  
-   [Sous-clés de spécification de pilote](../../../odbc/reference/install/driver-specification-subkeys.md)  
  
-   [Sous-clé du pilote par défaut](../../../odbc/reference/install/default-driver-subkey.md)  
  
-   [Sous-clé de convertisseurs ODBC](../../../odbc/reference/install/odbc-translators-subkey.md)  
  
-   [Sous-clés de spécification de convertisseur](../../../odbc/reference/install/translator-specification-subkeys.md)
