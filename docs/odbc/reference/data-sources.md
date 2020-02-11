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
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68135632"
---
# <a name="data-sources"></a>Sources de données
Une *source de données* est simplement la source des données. Il peut s’agir d’un fichier, d’une base de données particulière sur un SGBD ou même d’un flux de données actif. Les données peuvent se trouver sur le même ordinateur que le programme, ou sur un autre ordinateur sur un réseau. Par exemple, une source de données peut être un SGBD Oracle s’exécutant sur un système d’exploitation®, accessible par Novell® NetWare ; un SGBD IBM DB2 accessible via une passerelle ; collection de fichiers xbase dans un répertoire de serveur ; ou un fichier de base de données Microsoft® Access local.  
  
 L’objectif d’une source de données est de rassembler toutes les informations techniques nécessaires pour accéder aux données (le nom du pilote, l’adresse réseau, le logiciel réseau, etc.) à un emplacement unique et le masquer à l’utilisateur. L’utilisateur doit pouvoir consulter une liste incluant les salaires, l’inventaire et le personnel, choisir la paie dans la liste et demander à l’application de se connecter aux données de la paie, le tout sans savoir où se trouvent les données de la paie ou comment l’application les a obtenues.  
  
 Le terme « *source de données* » ne doit pas être confondu avec des termes similaires. Dans ce manuel, le *SGBD* ou la *base de données* fait référence à un moteur ou à un programme de base de données. Une autre distinction est faite entre les *bases de données de bureau,* conçues pour s’exécuter sur des ordinateurs personnels et souvent absentes de la prise en charge complète de SQL et des transactions, et les *bases de données de serveur,* conçues pour s’exécuter dans une situation client/serveur et caractérisées par un moteur de base de données autonome et une prise en charge complète des transactions et SQL. La *base de données* fait également référence à une collection de données particulière, telle qu’une collection de fichiers xbase dans un répertoire ou une base de données sur SQL Server. Il est généralement équivalent au terme *catalogue,* utilisé ailleurs dans ce manuel ou au *qualificateur* terme dans les versions antérieures d’ODBC.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Types de sources de données](../../odbc/reference/types-of-data-sources.md)  
  
-   [Utilisation des sources de données](../../odbc/reference/using-data-sources.md)  
  
-   [Exemple de source de données](../../odbc/reference/data-source-example.md)
