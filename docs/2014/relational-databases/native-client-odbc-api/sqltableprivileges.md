---
title: SQLTablePrivileges | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLTablePrivileges function
ms.assetid: 8cce22d5-28b1-4b50-a5bc-1de03e0ffd6b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 51492e55fd3c34c099a5f53187d1b2a9875ce7e3
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53349013"
---
# <a name="sqltableprivileges"></a>SQLTablePrivileges
  **SQLTablePrivileges** peut être exécutée sur un curseur statique. Une tentative d’exécution **SQLTablePrivileges** sur un actualisable (commandé par keyset ou dynamique) retourne SQL_SUCCESS_WITH_INFO pour indiquer que le type de curseur a été modifié.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge des informations de rapport pour les tables des serveurs liés en acceptant un nom en deux parties pour le *CatalogName* paramètre : *Nom_serveur_lié.Nom_Catalogue*.  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLTablePrivileges] (https://go.microsoft.com/fwlink/?LinkId=59373\)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
