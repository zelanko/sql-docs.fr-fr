---
title: Utilisation de l’authentification du système d’exploitation (en anglais seulement) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], authentication
- authentication [ODBC]
ms.assetid: 613daef7-3171-42d0-b7e3-3879280f864d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: d6520202bdbc31baf1156531457cb70a98656e88
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81292839"
---
# <a name="using-operating-system-authentication"></a>Utilisation de l’authentification du système d’exploitation
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 L’authentification du système d’exploitation Oracle repose sur le système d’exploitation sous-jacent pour contrôler l’accès aux comptes de base de données. Les utilisateurs n’ont pas besoin d’entrer un mot de passe lors de l’utilisation de ce type de connexion.  
  
 Pour profiter de cette fonctionnalité, spécifiez " /" comme identifiant utilisateur et ne spécifiez pas un mot de passe lors de la connexion à l’aide de l’une des interfaces AP: [SQLBrowseConnect](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md), [SQLConnect](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md), ou [SQLDriverConnect](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md).  
  
 Les bases de données Oracle utilisent les services d’authentification SQL-Net pour authentifier les utilisateurs connectés. Ce service fonctionne bien si les utilisateurs sont connectés à Oracle via SQLPlus; toutefois, lorsque l’utilisateur connecté est un service tel que les services d’information Sur Internet, l’authentification échoue. Il s’agit d’une limitation connue de SQL\*Net Authentication et produit l’erreur suivante: "[Microsoft][ODBC pilote pour Oracle][Oracle]ORA-12641: TNS:service d’authentification n’a pas réussi à initialiser."  
  
 Vous pouvez corriger ce problème en modifiant le fichier Sqlnet.ora. Ce fichier de configuration est généralement stocké dans la sous-direction réseau-Admin de l’annuaire à domicile Oracle. Ajouter la ligne suivante à Sqlnet.ora:  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```
