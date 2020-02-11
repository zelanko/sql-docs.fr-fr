---
title: Bibliothèque de curseurs ODBC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b81a7871434691a5940a04c7c60aaad9254b645
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "63201169"
---
# <a name="odbc-cursor-library"></a>Bibliothèque de curseurs ODBC
  Certains pilotes ODBC prennent uniquement en charge les paramètres de curseur par défaut ; Ces pilotes ne prennent pas non plus en charge les opérations de curseur positionnées, telles que **SQLSetPos**. La bibliothèque de curseurs ODBC est un composant de MDAC (Microsoft Data Access Components) qui permet d'implémenter des curseurs de bloc ou statiques sur un pilote qui ne les prend normalement pas en charge. La bibliothèque de curseurs implémente également les instructions UPDATE et DELETE positionnées et **SQLSetPos** pour les curseurs qu’elle crée.  
  
 La bibliothèque de curseurs ODBC est implémentée comme une couche entre le gestionnaire de pilotes ODBC et un pilote ODBC. Si la bibliothèque de curseurs ODBC est chargée, le Gestionnaire de pilote ODBC route toutes les commandes connexes à curseur à la bibliothèque de curseurs au lieu du pilote. La bibliothèque de curseurs implémente un curseur en extrayant l'intégralité du jeu de résultats du pilote sous-jacent et en mettant en cache le jeu de résultats sur le client. Lors de l'utilisation de la bibliothèque de curseurs ODBC, l'application est limitée aux fonctionnalités de curseur de la bibliothèque de curseurs ; toute prise en charge à des fonctionnalités de curseur supplémentaires dans le pilote sous-jacent n'est pas accessible à l'application.  
  
 L'utilisation de la bibliothèque de curseurs ODBC conjointement au pilote ODBC de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Native Client présente peu d'intérêt car le pilote prend en charge plus de fonctionnalités de curseur que la bibliothèque de curseurs ODBC. La seule raison d’utiliser la bibliothèque de curseurs ODBC [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec le pilote ODBC Native Client est que le pilote implémente sa prise en charge de curseur par le biais de curseurs côté serveur et que les curseurs côté serveur ne prennent pas en charge toutes les instructions SQL. Chaque fois qu'il est nécessaire d'avoir un curseur statique avec des procédures stockées, des lots ou des instructions SQL contenant COMPUTE, COMPUTE BY, FOR BROWSE ou INTO, songez à utiliser la bibliothèque de curseurs ODBC. Toutefois, utilisez-la avec précaution car elle met en cache l'intégralité du jeu de résultats sur le client, ce qui peut consommer de grandes quantités de mémoire et ralentir les performances.  
  
 Une application appelle la bibliothèque de curseurs connexion par connexion à l’aide de la fonction [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) pour définir l’attribut de connexion SQL_ATTR_ODBC_CURSORS avant de se connecter à une source de données. SQL_ATTR_ODBC_CURSORS prend l'une des trois valeurs suivantes :  
  
 SQL_CUR_USE_ODBC  
 Lorsque cette option est définie avec le [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] pilote ODBC Native Client, la bibliothèque de curseurs ODBC remplace la [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] prise en charge du curseur natif du pilote ODBC de Native Client. Seuls les types de curseurs pris en charge par la bibliothèque de curseurs peuvent être utilisés pour la connexion ; les curseurs côté serveur ne peuvent pas être utilisés.  
  
 SQL_CUR_USE_DRIVER  
 Lorsque cette option est définie, toute la prise en charge de curseur native [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] sur le pilote ODBC Native Client peut être utilisée pour la connexion. La bibliothèque de curseurs ODBC ne peut pas être utilisée. Tous les curseurs sont implémentés en tant que curseurs côté serveur.  
  
 SQL_CUR_USE_IF_NEEDED  
 Lorsque cette option est définie, l’effet est le même que SQL_CUR_USE_DRIVER lorsqu’il est utilisé [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] avec le pilote ODBC Native Client. Au moment de la connexion, le gestionnaire de pilotes ODBC effectue un test pour déterminer si le pilote ODBC qui est connecté prend en charge l’option SQL_FETCH_PRIOR de [SQLFetchScroll](../../native-client-odbc-api/sqlfetchscroll.md). Si le pilote ne prend pas en charge l'option, le gestionnaire de pilotes ODBC charge la bibliothèque de curseurs ODBC. Si le pilote prend en charge l'option, le gestionnaire de pilotes ODBC ne charge pas la bibliothèque de curseurs ODBC et l'application utilise la prise en charge native du pilote. Étant donné [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] que le pilote ODBC Native Client prend en charge SQL_FETCH_PRIOR, le gestionnaire de pilotes ODBC ne charge pas la bibliothèque de curseurs ODBC.  
  
 La bibliothèque de curseurs permet aux applications d'utiliser plusieurs instructions actives sur une connexion, ainsi que des curseurs déroulants pouvant être mis à jour. La bibliothèque de curseurs doit être chargée pour prendre en charge cette fonctionnalité. Utilisez [SQLSetConnectAttr](../../native-client-odbc-api/sqlsetconnectattr.md) pour spécifier comment la bibliothèque de curseurs doit être utilisée et [SQLSetStmtAttr](../../native-client-odbc-api/sqlsetstmtattr.md) pour spécifier le type de curseur, la concurrence et la taille de l’ensemble de lignes.  
  
## <a name="see-also"></a>Voir aussi  
 [Comment les curseurs sont implémentés](how-cursors-are-implemented.md)  
  
  
