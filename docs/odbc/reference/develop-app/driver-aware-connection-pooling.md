---
description: Regroupement de connexions prenant en charge les pilotes
title: Regroupement de connexions prenant en charge les pilotes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 53e7e3f7-edab-4d0b-8943-45442ba3ebc9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ed2fa29a68095be9cfcc7d4192c6dc2e15f3eac7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88494657"
---
# <a name="driver-aware-connection-pooling"></a>Regroupement de connexions prenant en charge les pilotes
Le regroupement de connexions prenant en charge les pilotes est une nouvelle fonctionnalité du gestionnaire de pilotes dans Windows 8. Le regroupement de connexions prenant en charge les pilotes permet aux créateurs de pilotes de personnaliser le comportement de regroupement de connexions dans leur pilote ODBC.  
  
> [!NOTE]  
>  Le regroupement de connexions prenant en charge les pilotes n’est pas pris en charge avec la bibliothèque de curseurs. Une application recevra un message d’erreur si elle tente d’activer la bibliothèque de curseurs via SQLSetConnectAttr, lorsque le regroupement de connexions prenant en charge les pilotes est activé.  
  
 Le regroupement de connexions prenant en charge les pilotes résout les problèmes suivants liés au regroupement de connexions du gestionnaire de pilotes :  
  
 **Fragmentation de pool** Le gestionnaire de pilotes renvoie une connexion à partir du pool uniquement s’il s’agit d’une correspondance exacte avec la chaîne de connexion d’une nouvelle demande de connexion.  L’une des raisons pour lesquelles le gestionnaire de pilote peut exiger une correspondance exacte est que le gestionnaire de pilotes ne comprend pas tous les mots clés de chaîne de connexion spécifiques au pilote et sa valeur.  Toutefois, certaines valeurs de mot clé de chaîne de connexion (telles que le nom de la base de données) peuvent ne pas nécessiter une correspondance exacte, puisque le pilote peut modifier la base de données en moins du temps nécessaire à l’ouverture d’une nouvelle connexion (la différence d’heure exacte dépend de la source de données). En outre, les différences entre certains attributs de connexion (par exemple SQL_ATTR_CURRENT_CATALOG) peuvent prendre plus de temps que les différences dans d’autres attributs (comme SQL_ATTR_LOGIN_TIMEOUT). Cela peut également empêcher le gestionnaire de pilotes d’utiliser la connexion la plus économique et réutilisable à partir du pool. Lorsqu’un pilote doit créer de nombreuses connexions, les performances d’une application peuvent diminuer et l’évolutivité de la source de données peut diminuer. La fragmentation de pool peut être réduite avec le regroupement de connexions prenant en charge les pilotes, car un pilote peut mieux estimer le coût de la réutilisation d’une connexion dans le pool pour une demande de connexion.  
  
 **Aucun examen de la préférence de l’application** Certaines sources de données peuvent ouvrir efficacement de nouvelles connexions (par rapport à la réinitialisation de certains attributs). par conséquent, une application peut préférer ouvrir une nouvelle connexion au lieu de tenter de réutiliser une connexion légèrement incompatible à partir du pool et de réinitialiser certaines valeurs (même si cela peut être plus lent pendant l’expression d’initialisation du pool de connexions). Toutefois, certaines applications peuvent réduire la charge du serveur et ouvrir moins de connexions, bien qu’il puisse y avoir un coût plus important pour résoudre les incompatibilités pour un comportement correct. Sans regroupement de connexions prenant en charge les pilotes, vous ne pouvez pas spécifier ce type de préférence de manière efficace, car le gestionnaire de pilotes ne reconnaît pas tous les attributs de connexion spécifiques au pilote. Le regroupement de connexions prenant en charge les pilotes permet à un pilote d’obtenir la préférence de l’utilisateur (avec un attribut spécifique au pilote SQLSetConnectAttr) afin de mieux estimer le coût de la réutilisation d’une connexion à partir du pool en fonction des préférences de l’utilisateur.  
  
 Pour plus d’informations sur le regroupement de connexions prenant en charge les pilotes, consultez [développement de la reconnaissance des pools de connexions dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
## <a name="determining-driver-support"></a>Détermination de la prise en charge des pilotes  
 Le regroupement de connexions prenant en charge les pilotes est une fonctionnalité facultative qu’un pilote peut ne pas prendre en charge. Pour déterminer si un pilote le prend en charge, utilisez l' *InfoType* SQL_DRIVER_AWARE_POOLING_SUPPORTED de [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
## <a name="how-to-enable-driver-aware-connection-pooling"></a>Comment activer le regroupement de connexions prenant en charge les pilotes  
 Une application peut utiliser la sensibilisation à la mise en pool des connexions d’un pilote en affectant à l’attribut SQL_ATTR_CONNECTION_POOLING la valeur SQL_CP_DRIVER_AWARE avec [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md). Si un pilote ne prend pas en charge la reconnaissance des pools de connexions, le regroupement de connexions du gestionnaire de pilotes sera utilisé (comme si SQL_CP_ONE_PER_HENV avait été spécifié, au lieu de SQL_CP_DRIVER_AWARE). Les applications ODBC 2. x et 3. x peuvent activer cette fonctionnalité.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
