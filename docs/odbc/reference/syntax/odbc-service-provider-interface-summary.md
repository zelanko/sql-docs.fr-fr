---
title: Résumé de l’interface des fournisseurs de services de l’ODBC (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ace6085b-355b-435b-8734-503fc3c12ec2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b2f7e459cc7b89106bf1b7ebcd49c699d43da9f6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298896"
---
# <a name="odbc-service-provider-interface-summary"></a>Récapitulatif sur l’interface SPI ODBC
Le tableau suivant décrit les fonctions d’interface ODBC Service Provider. Pour plus d’informations sur la syntaxe et la sémantique pour chaque fonction, voir [ODBC Service Provider Interface (SPI) Référence](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md).  
  
|Nom de la fonction|Objectif|  
|-------------------|-------------|  
|[SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Même que [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), mais il définit l’attribut sur le jeton d’informations de connexion au lieu de sur la poignée de connexion.|  
|[SQLSetDriverConnectInfo (en anglais)](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|Définit la chaîne de connexion dans le jeton d’information de connexion pour l’appel [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) d’une application.|  
|[SQLSetConnectInfo (en anglais)](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Définit la source de données, l’identifiant d’utilisateur et le mot de passe dans le jeton d’information de connexion pour l’appel [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) d’une application.|  
|[SQLGetPoolID (SQLGetPoolID)](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Récupère l’ID de la piscine.|  
|[SQLRateConnection (SQLRateConnection)](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Détermine si un conducteur peut réutiliser une connexion existante dans le pool de connexion.|  
|[SQLPoolConnect (SQLPoolConnect)](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Créez une nouvelle connexion si aucune connexion dans la piscine ne peut être réutilisée.|  
|[SQLCleanupConnectionPoolID (EN anglais)](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Informe un conducteur qu’une pièce d’identité de piscine a été chronométrée.|
