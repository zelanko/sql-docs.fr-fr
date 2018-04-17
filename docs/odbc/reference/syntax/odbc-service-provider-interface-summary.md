---
title: Résumé de Interface du fournisseur de Service ODBC | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ace6085b-355b-435b-8734-503fc3c12ec2
caps.latest.revision: 4
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 60cd51075100f77e131e3a9e48dbdf2d10a444b8
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="odbc-service-provider-interface-summary"></a>Résumé de Interface du fournisseur de Service ODBC
Le tableau suivant décrit les fonctions d’interface de fournisseur de Service ODBC. Pour plus d’informations sur la syntaxe et la sémantique pour chaque fonction, consultez [référence de l’Interface de fournisseur de Service ODBC (SPI)](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md).  
  
|Nom de la fonction|Fonction|  
|-------------------|-------------|  
|[SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Identique à [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), mais il définit l’attribut sur le jeton d’informations de connexion à la place de sur le handle de connexion.|  
|[SQLSetDriverConnectInfo](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|Définit la chaîne de connexion dans le jeton d’informations de connexion pour une application [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) appeler.|  
|[SQLSetConnectInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Définit la source de données, un ID d’utilisateur et un mot de passe dans le jeton d’informations de connexion pour une application [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) appeler.|  
|[SQLGetPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Récupère l’ID de pool.|  
|[SQLRateConnection](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Détermine si un pilote peut réutiliser une connexion existante dans le pool de connexions.|  
|[SQLPoolConnect](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Créer une nouvelle connexion si aucune connexion dans le pool ne peut être réutilisée.|  
|[SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Informe un pilote qui a un ID du pool a été dépassé.|
