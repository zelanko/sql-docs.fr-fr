---
title: Entrées de Registre pour les composants ODBC | Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bead63f11b253342cd444e1d5bd0697ee00cfbc1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81296179"
---
# <a name="registry-entries-for-odbc-components"></a>Entrées de Registre pour les composants ODBC
> [!NOTE]  
>  À compter de Windows XP et de Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous devez uniquement installer explicitement ODBC sur les versions antérieures de Windows.  
  
 La DLL du programme d’installation gère les informations du Registre relatives à chaque composant ODBC installé. Sur les ordinateurs exécutant Microsoft Windows NT et Microsoft Windows 95/98, ces informations sont stockées dans des sous-clés sous la clé suivante dans le registre :  

 ```console
 HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\Odbcinst.ini
 ```

 Comme Odbcinst. ini est une sous-clé de l’arborescence HKEY_LOCAL_MACHINE, les informations sur les composants ODBC sont accessibles à tous les utilisateurs de l’ordinateur.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Sous-clé des composants principaux ODBC](../../../odbc/reference/install/odbc-core-subkey.md)  
  
-   [Sous-clé des pilotes ODBC](../../../odbc/reference/install/odbc-drivers-subkey.md)  
  
-   [Sous-clés de spécification de pilote](../../../odbc/reference/install/driver-specification-subkeys.md)  
  
-   [Sous-clé du pilote par défaut](../../../odbc/reference/install/default-driver-subkey.md)  
  
-   [Sous-clé de convertisseurs ODBC](../../../odbc/reference/install/odbc-translators-subkey.md)  
  
-   [Sous-clés de spécification de convertisseur](../../../odbc/reference/install/translator-specification-subkeys.md)
