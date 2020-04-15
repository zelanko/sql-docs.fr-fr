---
title: Bibliothèque de cursors de l’ODBC (fr) Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- cursors [ODBC], library
- SQL_CUR_USE_DRIVER option
- ODBC applications, cursors
- ODBC cursors, library
- SQL_CUR_USE_IF_NEEDED option
- SQLSetConnectAttr function
- SQL_CUR_USE_ODBC option
ms.assetid: 3c610d3d-6e06-49cf-9a40-05b6a1c83a32
author: markingmyname
ms.author: maghan
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 93c85bc943d1a6a081cbea6bbeae40ba85aeffc5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305389"
---
# <a name="odbc-cursor-library"></a>Bibliothèque de curseurs ODBC
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

  Certains conducteurs d’ODBC ne prennent en charge que les paramètres de curseur par défaut; ces conducteurs ne prennent pas non plus en charge les opérations de curseur positionné, comme **SQLSetPos**. La bibliothèque de curseurs ODBC est un composant de MDAC (Microsoft Data Access Components) qui permet d'implémenter des curseurs de bloc ou statiques sur un pilote qui ne les prend normalement pas en charge. La bibliothèque de curseurs implémente également les relevés UPDATE et DELETE positionnés et **SQLSetPos** pour les curseurs qu’elle crée.  
  
 La bibliothèque de curseurs ODBC est implémentée comme une couche entre le gestionnaire de pilotes ODBC et un pilote ODBC. Si la bibliothèque de curseurs ODBC est chargée, le Gestionnaire de pilote ODBC route toutes les commandes connexes à curseur à la bibliothèque de curseurs au lieu du pilote. La bibliothèque de curseurs implémente un curseur en extrayant l'intégralité du jeu de résultats du pilote sous-jacent et en mettant en cache le jeu de résultats sur le client. Lors de l'utilisation de la bibliothèque de curseurs ODBC, l'application est limitée aux fonctionnalités de curseur de la bibliothèque de curseurs ; toute prise en charge à des fonctionnalités de curseur supplémentaires dans le pilote sous-jacent n'est pas accessible à l'application.  
  
 L'utilisation de la bibliothèque de curseurs ODBC conjointement au pilote ODBC de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client présente peu d'intérêt car le pilote prend en charge plus de fonctionnalités de curseur que la bibliothèque de curseurs ODBC. La seule raison d’utiliser la bibliothèque de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] curseurs ODBC avec le pilote Native Client ODBC est parce que le conducteur implémente son support curseur par le biais de curseurs serveur, et les curseurs de serveur ne prennent pas en charge toutes les déclarations SQL. Chaque fois qu'il est nécessaire d'avoir un curseur statique avec des procédures stockées, des lots ou des instructions SQL contenant COMPUTE, COMPUTE BY, FOR BROWSE ou INTO, songez à utiliser la bibliothèque de curseurs ODBC. Toutefois, utilisez-la avec précaution car elle met en cache l'intégralité du jeu de résultats sur le client, ce qui peut consommer de grandes quantités de mémoire et ralentir les performances.  
  
 Une application invoque la bibliothèque de curseurs sur une base de connexion par connexion en utilisant [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) pour définir l’attribut de connexion SQL_ATTR_ODBC_CURSORS avant de se connecter à une source de données. SQL_ATTR_ODBC_CURSORS prend l'une des trois valeurs suivantes :  
  
 SQL_CUR_USE_ODBC  
 Lorsque cette option est [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] définie avec le conducteur de Native Client ODBC, [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] la bibliothèque de curseurs ODBC remplace le soutien du curseur natif du conducteur ODBC. Seuls les types de curseurs pris en charge par la bibliothèque de curseurs peuvent être utilisés pour la connexion ; les curseurs côté serveur ne peuvent pas être utilisés.  
  
 SQL_CUR_USE_DRIVER  
 Lorsque cette option est définie, tous les soutiens du curseur originaires du [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] conducteur native ODBC peuvent être utilisés pour la connexion. La bibliothèque de curseurs ODBC ne peut pas être utilisée. Tous les curseurs sont implémentés en tant que curseurs côté serveur.  
  
 SQL_CUR_USE_IF_NEEDED  
 Lorsque cette option est définie, l’effet est le même [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que SQL_CUR_USE_DRIVER lorsqu’il est utilisé avec le conducteur native ODBC client. À l’heure de connexion, le gestionnaire de conducteur de l’ODBC teste si le conducteur de l’ODBC étant connecté pour prendre en charge l’option SQL_FETCH_PRIOR de [SQLFetchScroll](../../../relational-databases/native-client-odbc-api/sqlfetchscroll.md). Si le pilote ne prend pas en charge l'option, le gestionnaire de pilotes ODBC charge la bibliothèque de curseurs ODBC. Si le pilote prend en charge l'option, le gestionnaire de pilotes ODBC ne charge pas la bibliothèque de curseurs ODBC et l'application utilise la prise en charge native du pilote. Étant [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] donné que le conducteur de Native Client ODBC prend en charge SQL_FETCH_PRIOR, le gestionnaire de conduite de l’ODBC ne charge pas la bibliothèque de curseurs de l’ODBC.  
  
 La bibliothèque de curseurs permet aux applications d'utiliser plusieurs instructions actives sur une connexion, ainsi que des curseurs déroulants pouvant être mis à jour. La bibliothèque de curseurs doit être chargée pour prendre en charge cette fonctionnalité. Utilisez [SQLSetConnectAttr](../../../relational-databases/native-client-odbc-api/sqlsetconnectattr.md) pour spécifier comment la bibliothèque de curseurs doit être utilisée et [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) pour spécifier le type de curseur, la concordance et la taille de l’aviron.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment les curseurs sont implémentés](../../../relational-databases/native-client-odbc-cursors/implementation/how-cursors-are-implemented.md)  
  
  
