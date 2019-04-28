---
title: Le regroupement de connexions prenant en charge les pilotes | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 53e7e3f7-edab-4d0b-8943-45442ba3ebc9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 8ea4643354990ad416ac3975467c5991842adacc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62658255"
---
# <a name="driver-aware-connection-pooling"></a>Regroupement de connexions prenant en charge les pilotes
Le regroupement de connexions prenant en charge de pilote est une nouvelle fonctionnalité du Gestionnaire de pilotes dans Windows 8. Le regroupement de connexions prenant en charge de pilote permet les rédacteurs de pilotes personnaliser la comportement dans leurs pilotes ODBC de regroupement de connexions.  
  
> [!NOTE]  
>  Le regroupement de connexions prenant en charge de pilote n’est pas pris en charge avec la bibliothèque de curseurs. Une application message d’erreur si elle tente d’activer la bibliothèque de curseurs par le biais de SQLSetConnectAttr, lorsque le regroupement de connexions prenant en charge de pilote est activé.  
  
 Pilote prenant en charge le regroupement de connexions adresses les problèmes suivants liés au regroupement de connexions de gestionnaire de pilotes :  
  
 **Fragmentation de pool** le Gestionnaire de pilote retournera uniquement une connexion à partir du pool dans le cas d’une correspondance exacte avec la chaîne de connexion d’une nouvelle demande de connexion.  L’une des raisons pour le Gestionnaire de pilotes pour exiger une correspondance exacte sont que le Gestionnaire de pilotes ne comprend pas de chaque mot de clé de chaîne de connexion spécifiques au pilote et sa valeur.  Toutefois, certaines valeurs de mot clé de chaîne de connexion (par exemple, le nom de la base de données) ne peuvent pas nécessiter une correspondance exacte, étant donné que le pilote peut changer la base de données inférieur au temps nécessaire pour ouvrir une nouvelle connexion (la différence de temps exact dépend de la source de données). Et, les différences de certains attributs de connexion (par exemple, SQL_ATTR_CURRENT_CATALOG) peuvent prendre plus de temps pour modifier que les différences dans les autres attributs (par exemple, sql_attr_login_timeout permet de contrôler). Cela, trop, peut empêcher le Gestionnaire de pilotes à l’aide de la connexion plus économique et réutilisable à partir du pool. Lorsqu’un pilote a créer de nouvelles connexions, les performances d’une application peuvent diminuer et l’évolutivité de source de données peut diminuer. Fragmentation de pool peut être réduite avec le regroupement de connexions prenant en charge de pilote, car un pilote peut mieux estimer le coût de réutiliser une connexion dans le pool pour une demande de connexion.  
  
 **Aucune attention de préférence de l’application** certaines sources de données peuvent ouvrir efficacement de nouvelles connexions (par rapport à la réinitialisation de certains attributs), par conséquent, une application peut préférer ouvrir une nouvelle connexion au lieu de tenter de réutiliser un légèrement incompatibles connexion à partir du pool et la réinitialisation de certaines valeurs (bien que cela peut être plus lent lors de l’expression de l’initialisation de pool de connexion). Mais certaines applications peuvent conserver la charge du serveur plus petits et ouvrir des connexions moins, bien qu’il peut y avoir un coût plus important pour résoudre les incompatibilités pour le comportement correct. Sans le regroupement de connexions prenant en charge de pilote, vous ne pouvez pas spécifier ce genre de préférence efficacement, car le Gestionnaire de pilotes ne reconnaît pas tous les attributs de connexion spécifiques au pilote. Le regroupement de connexions prenant en charge de pilote permet à un pilote obtenir la préférence utilisateur (avec un attribut spécifique au pilote de SQLSetConnectAttr) afin qu’il peut mieux estimer le coût de réutiliser une connexion à partir du pool en fonction de préférences de l’utilisateur.  
  
 Pour plus d’informations sur le regroupement de connexions prenant en charge les pilotes, consultez [développer la reconnaissance des pools de connexion dans un pilote ODBC](../../../odbc/reference/develop-driver/developing-connection-pool-awareness-in-an-odbc-driver.md).  
  
## <a name="determining-driver-support"></a>Déterminer les pilotes pris en charge  
 Le regroupement de connexions prenant en charge de pilote est une fonctionnalité facultative qui un pilote ne peut pas prendre en charge. Pour déterminer si un pilote prend en charge, utilisez le SQL_DRIVER_AWARE_POOLING_SUPPORTED *InfoType* de [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md).  
  
## <a name="how-to-enable-driver-aware-connection-pooling"></a>Comment activer le regroupement de connexions prenant en charge de pilote  
 Une application peut utiliser la reconnaissance de regroupement de connexions d’un pilote en définissant l’attribut SQL_ATTR_CONNECTION_POOLING sur SQL_CP_DRIVER_AWARE avec [SQLSetEnvAttr](../../../odbc/reference/syntax/sqlsetenvattr-function.md). Si un pilote ne prend pas en charge la reconnaissance des pools de connexion, le regroupement de connexions de gestionnaire de pilotes sera utilisé (même comme si SQL_CP_ONE_PER_HENV avait été spécifié, au lieu de SQL_CP_DRIVER_AWARE). Les applications ODBC 2.x et 3.x peuvent activer cette fonctionnalité.  
  
## <a name="see-also"></a>Voir aussi  
 [Développement d’un pilote ODBC](../../../odbc/reference/develop-driver/developing-an-odbc-driver.md)
