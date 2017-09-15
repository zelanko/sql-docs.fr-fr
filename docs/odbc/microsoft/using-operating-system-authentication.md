---
title: "À l’aide de l’authentification du système d’exploitation | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC driver for Oracle [ODBC], authentication
- authentication [ODBC]
ms.assetid: 613daef7-3171-42d0-b7e3-3879280f864d
caps.latest.revision: 8
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: d3fbe8f4ce9fe9edbb88c7c895311bd9560dc28f
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="using-operating-system-authentication"></a>À l’aide de l’authentification du système d’exploitation
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 L’authentification du système d’exploitation Oracle repose sur le système d’exploitation sous-jacent pour contrôler l’accès aux comptes de la base de données. Les utilisateurs ne doivent pas entrer un mot de passe lors de l’utilisation de ce type de connexion.  
  
 Pour tirer parti de cette fonctionnalité, spécifiez « / » en tant que l’ID d’utilisateur et ne spécifiez pas un mot de passe lors de la connexion à l’aide de l’API de connexion suivante : [SQLBrowseConnect](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md), [SQLConnect](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md), ou [SQLDriverConnect](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md).  
  
 Utilisent de bases de données Oracle SQL * Net Services d’authentification pour authentifier les utilisateurs qui sont connectés. Ce service fonctionne correctement si les utilisateurs sont connectés dans Oracle via SQLPlus ; Toutefois, lorsque l’utilisateur connecté est un service tel qu’Internet Information Services, l’authentification échoue. Il s’agit d’une limitation connue de SQL\*réseau l’authentification et génère l’erreur suivante : « [Microsoft] [pilote ODBC pour Oracle] [Oracle] ORA-12641 : échec d’initialisation TNS:authentication service. »  
  
 Vous pouvez corriger ce problème en modifiant le fichier Sqlnet.ora. Ce fichier de configuration est généralement stocké dans le sous-répertoire Network\Admin du répertoire racine Oracle. Ajoutez la ligne suivante à Sqlnet.ora :  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```
