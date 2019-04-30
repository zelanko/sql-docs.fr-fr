---
title: À l’aide de l’authentification du système d’exploitation | Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 5a532c253ea2204fa3636c24c503cbefd3fa6311
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63127810"
---
# <a name="using-operating-system-authentication"></a>Utilisation de l’authentification du système d’exploitation
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Au lieu de cela, utilisez le pilote ODBC fourni par Oracle.  
  
 L’authentification du système d’exploitation Oracle s’appuie sur le système d’exploitation sous-jacent pour contrôler l’accès aux comptes de base de données. Les utilisateurs ne doivent pas entrer un mot de passe lors de l’utilisation de ce type de connexion.  
  
 Pour tirer parti de cette fonctionnalité, spécifiez « / » en tant que l’ID d’utilisateur et ne spécifiez pas un mot de passe lors de la connexion à l’aide de l’API de connexion suivante : [SQLBrowseConnect](../../odbc/microsoft/level-2-api-functions-odbc-driver-for-oracle.md), [SQLConnect](../../odbc/microsoft/core-level-api-functions-odbc-driver-for-oracle.md), ou [SQLDriverConnect](../../odbc/microsoft/level-1-api-functions-odbc-driver-for-oracle.md).  
  
 Utilisent de bases de données Oracle SQL * Net Services d’authentification pour authentifier les utilisateurs qui sont connectés. Ce service fonctionne bien si les utilisateurs sont connectés à Oracle via SQLPlus ; Toutefois, lorsque l’utilisateur connecté est un service tel qu’Internet Information Services, l’authentification échoue. Il s’agit d’une limitation connue de SQL\*authentification Net et génère l’erreur suivante : « [Microsoft] [pilote ODBC pour Oracle] [Oracle] ORA-12641 : Service de TNS:Authentication initialisation a échoué. »  
  
 Vous pouvez corriger ce problème en modifiant le fichier Sqlnet.ora. Ce fichier de configuration est généralement stocké dans le sous-répertoire Network\Admin du répertoire racine Oracle. Ajoutez la ligne suivante à Sqlnet.ora :  
  
```  
SQLNET.AUTHENTICATION_SERVICES = (none)  
```
