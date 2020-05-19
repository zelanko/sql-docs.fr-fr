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
author: rothja
ms.author: jroth
manager: craigg
ms.openlocfilehash: 03c19fecd314bd67949b133e6c1e0ae9e8292d3d
ms.sourcegitcommit: b72c9fc9436c44c6a21fd96223c73bf94706c06b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/01/2020
ms.locfileid: "82705851"
---
# <a name="sqltableprivileges"></a>SQLTablePrivileges
  **SQLTablePrivileges** peut être exécuté sur un curseur statique. Une tentative d’exécution de **SQLTablePrivileges** sur un qui peut être mis à jour (KEYSET ou Dynamic) retourne SQL_SUCCESS_WITH_INFO indiquant que le type de curseur a été modifié.  
  
 Le pilote ODBC [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client prend en charge les informations de création de rapport pour les tables des serveurs liés en acceptant un nom en deux parties pour le paramètre *CatalogName* : *Linked_Server_Name.Catalog_Name*.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLTablePrivileges fonction] (https://go.microsoft.com/fwlink/?LinkId=59373\)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
