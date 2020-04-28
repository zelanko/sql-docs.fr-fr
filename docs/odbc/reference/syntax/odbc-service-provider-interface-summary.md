---
title: Résumé de l’interface du fournisseur de services ODBC | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298896"
---
# <a name="odbc-service-provider-interface-summary"></a>Récapitulatif sur l’interface SPI ODBC
Le tableau suivant décrit les fonctions de l’interface du fournisseur de service ODBC. Pour plus d’informations sur la syntaxe et la sémantique de chaque fonction, consultez Référence de l' [interface SPI (Service Provider Interface) ODBC](../../../odbc/reference/syntax/odbc-service-provider-interface-spi-reference.md).  
  
|Nom de la fonction|Objectif|  
|-------------------|-------------|  
|[SQLSetConnectAttrForDbcInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Identique à [SQLSetConnectAttr](../../../odbc/reference/syntax/sqlsetconnectattr-function.md), mais définit l’attribut sur le jeton d’informations de connexion plutôt que sur le handle de connexion.|  
|[SQLSetDriverConnectInfo](../../../odbc/reference/syntax/sqldrivertodatasource-function.md)|Définit la chaîne de connexion dans le jeton d’informations de connexion pour l’appel de [SQLDriverConnect](../../../odbc/reference/syntax/sqldriverconnect-function.md) d’une application.|  
|[SQLSetConnectInfo](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Définit la source de données, l’ID d’utilisateur et le mot de passe dans le jeton d’informations de connexion pour l’appel de [SQLConnect](../../../odbc/reference/syntax/sqlconnect-function.md) d’une application.|  
|[SQLGetPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Récupère l’ID du pool.|  
|[SQLRateConnection](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Détermine si un pilote peut réutiliser une connexion existante dans le pool de connexions.|  
|[SQLPoolConnect](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Créez une nouvelle connexion si aucune connexion dans le pool ne peut être réutilisée.|  
|[SQLCleanupConnectionPoolID](../../../odbc/reference/syntax/sqldatasourcetodriver-function.md)|Informe un pilote qu’un ID de pool a dépassé le délai d’attente.|
