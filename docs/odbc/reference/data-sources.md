---
title: Sources de données | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC]
- data sources [ODBC], about data sources
ms.assetid: 4ae44fa2-0b9b-4e19-ab45-c1dc93b68406
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 92b8ca2b8c780e48cd9f3bf815ca86e3bd27081e
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68135632"
---
# <a name="data-sources"></a>Sources de données
Un *source de données* est simplement la source des données. Il peut être un fichier, une base de données sur un système SGBD, ou même un flux de données actives. Les données peuvent être situées sur le même ordinateur que le programme ou sur un autre ordinateur situé sur un réseau. Par exemple, une source de données peut être un SGBD Oracle s’exécutant sur un système d’exploitation OS/2®, accédé par Novell Netware,® ; un SGBD de DB2 d’IBM accessibles via une passerelle ; une collection de fichiers Xbase dans un répertoire du serveur ; ou un fichier de base de données Microsoft® Access local.  
  
 L’objectif d’une source de données consiste à rassembler toutes les informations techniques nécessaires pour accéder aux données - le nom du pilote, adresse réseau, un logiciel réseau et ainsi de suite - dans un emplacement unique et masquez-la par rapport à l’utilisateur. L’utilisateur doit être en mesure de consulter la liste qui inclut les salaires, l’inventaire et le Personnel, choisissez paie à partir de la liste et que l’application de se connecter aux données de paie, tout cela sans savoir où résident les données de paie ou comment l’application a obtenu à celui-ci.  
  
 Le terme *source de données* ne doit pas être confondu avec les termes similaires. Dans ce manuel, *SGBD* ou *base de données* fait référence à un programme de base de données ou d’un moteur. Encore une différence est faite entre *des bases de données bureautiques,* conçu pour s’exécuter sur les ordinateurs personnels et souvent pauvre dans SQL complète et prise en charge de la transaction, et *bases de données de serveur,* conçu pour s’exécuter dans un client / situation de serveur et caractérisée par un moteur de base de données autonome et SQL riche et de prise en charge de la transaction. *Base de données* fait également référence à un regroupement particulier de données, telle qu’une collection de fichiers Xbase dans un répertoire ou d’une base de données sur SQL Server. Il est généralement équivalent au terme de *catalogue,* utilisée ailleurs dans ce manuel ou le terme *qualificateur* dans les versions antérieures d’ODBC.  
  
 Cette section contient les rubriques suivantes.  
  
-   [Types de sources de données](../../odbc/reference/types-of-data-sources.md)  
  
-   [Utilisation des sources de données](../../odbc/reference/using-data-sources.md)  
  
-   [Exemple de source de données](../../odbc/reference/data-source-example.md)
