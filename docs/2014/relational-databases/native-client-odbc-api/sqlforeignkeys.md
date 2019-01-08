---
title: SQLForeignKeys | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
topic_type:
- apiref
helpviewer_keywords:
- SQLForeignKeys function
ms.assetid: 6c01ce0d-30d7-4c86-8705-3ab254d8a845
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8481b0f19566ed0e55f31480f9ab8be0c9441c7d
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2018
ms.locfileid: "53360441"
---
# <a name="sqlforeignkeys"></a>SQLForeignKeys
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] prend en charge les mises à jour en cascade et les suppressions via le mécanisme de contrainte de clé étrangère. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne SQL_CASCADE pour les colonnes UPDATE_RULE et/ou DELETE_RULE si l'option CASCADE est spécifiée dans la clause ON UPDATE et/ou ON DELETE des contraintes FOREIGN KEY. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] retourne SQL_NO_ACTION pour les colonnes UPDATE_RULE et/ou DELETE_RULE si l'option NO ACTION est spécifiée dans la clause ON UPDATE et/ou ON DELETE des contraintes FOREIGN KEY.  
  
 Lorsque les valeurs non valides sont présentes dans un **SQLForeignKeys** paramètre, **SQLForeignKeys** retourne SQL_SUCCESS à l’exécution. **SQLFetch** retourne SQL_NO_DATA lorsque des valeurs non valides sont utilisées dans ces paramètres.  
  
 **SQLForeignKeys** peut être exécutée sur un curseur côté serveur statique. Une tentative d’exécution **SQLForeignKeys** sur un curseur modifiable (dynamique ou jeu de clés) retourne SQL_SUCCESS_WITH_INFO, indiquant que le type de curseur a été modifié.  
  
 Le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pilote ODBC Native Client prend en charge des informations de rapport pour les tables des serveurs liés en acceptant un nom en deux parties pour le *FKCatalogName* et *PKCatalogName* paramètres : *Nom_serveur_lié.Nom_Catalogue*.  
  
## <a name="see-also"></a>Voir aussi  
 [SQLForeignKeys (fonction)](https://go.microsoft.com/fwlink/?LinkId=59344)   
 [Détails de l’implémentation d’API ODBC](odbc-api-implementation-details.md)  
  
  
