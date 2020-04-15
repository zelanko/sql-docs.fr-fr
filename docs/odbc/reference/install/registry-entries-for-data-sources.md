---
title: Inscriptions au registre des sources de données (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- subkeys [ODBC]
- data sources [ODBC], registry entries
- registry entries for data sources [ODBC], about registry entries
- data sources [ODBC], configuring
- registry entries for data sources [ODBC]
ms.assetid: 78aaa3d3-d081-4550-80e3-720c910d5996
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: c73ea704b091bc37afb1ac42b520304022d929c3
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81296269"
---
# <a name="registry-entries-for-data-sources"></a>Entrées de Registre pour les sources de données
> [!NOTE]  
>  En commençant par Windows XP et Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous ne devez installer explicitement ODBC que sur les versions antérieures de Windows.  
  
 L’installateur DLL conserve des informations dans le registre sur chaque source de données. Dans Microsoft Windows NT/Windows 2000 et Microsoft Windows 95/98, ces informations sont stockées dans des sous-clés sous l’une des deux clés suivantes du registre :  

 ```console
 HKEY_LOCAL_MACHINE\SOFTWARE\ODBC\Odbc.ini  
 ```

 ```console
 HKEY_CURRENT_USER\SOFTWARE\ODBC\Odbc.ini
 ```

 La clé utilisée dépend si la source de données est une *source de données système,* qui est disponible pour tous les utilisateurs, ou une *source de données utilisateur,* qui n’est disponible que pour l’utilisateur actuel. Les sources de données du système sont stockées sur l’arbre HKEY_LOCAL_MACHINE, et les sources de données utilisateur sont stockées sur l’arbre HKEY_CURRENT_USER. À tous les autres égards, les sources de données système et les sources de données utilisateur sont identiques.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Sous-clé des sources de données ODBC](../../../odbc/reference/install/odbc-data-sources-subkey.md)  
  
-   [Sous-clés de spécification de source de données](../../../odbc/reference/install/data-source-specification-subkeys.md)  
  
-   [Sous-clé par défaut](../../../odbc/reference/install/default-subkey.md)  
  
-   [Sous-clé ODBC](../../../odbc/reference/install/odbc-subkey.md)
