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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9b7e464963471b0cad41c5b93d50507d0fa9bf96
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306510"
---
# <a name="data-sources"></a>Sources de données
Une *source de données* est simplement la source des données. Il peut s’agir d’un fichier, d’une base de données particulière sur un DBMS ou même d’un flux de données en direct. Les données peuvent être localisées sur le même ordinateur que le programme, ou sur un autre ordinateur quelque part sur un réseau. Par exemple, une source de données peut être un DBMS Oracle fonctionnant sur un système d’exploitation OS/2®, accessible par Novell® Netware; un DBMS IBM DB2 accessible par une passerelle; une collection de fichiers Xbase dans un répertoire de serveur; ou un fichier local de base de données Microsoft® Access.  
  
 Le but d’une source de données est de rassembler toutes les informations techniques nécessaires pour accéder aux données - le nom du conducteur, l’adresse réseau, le logiciel réseau, etc . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . . L’utilisateur devrait être en mesure d’examiner une liste qui comprend la paie, l’inventaire et le personnel, choisir la paie de la liste, et avoir l’application se connecter aux données de paie, le tout sans savoir où les données de paie réside ou comment l’application est arrivé à elle.  
  
 Le terme *source de données* ne doit pas être confondu avec des termes similaires. Dans ce manuel, *DBMS* ou *base de données* se réfère à un programme de base de données ou un moteur. Une autre distinction est faite entre *les bases de données de bureau,* conçues pour fonctionner sur des ordinateurs personnels et souvent dépourvues de soutien complet SQL et transaction, et les bases de données de *serveur,* conçus pour fonctionner dans une situation client /serveur et caractérisé par un moteur de base de données autonome et riche SQL et le support transactionnel. *La base* de données fait également référence à une collecte particulière de données, comme la collecte de fichiers Xbase dans un répertoire ou une base de données sur SQL Server. Il est généralement équivalent au *terme catalogue,* utilisé ailleurs dans ce manuel, ou le terme *qualificatif* dans les versions antérieures de l’ODBC.  
  
 Cette section contient les rubriques suivantes :  
  
-   [Types de sources de données](../../odbc/reference/types-of-data-sources.md)  
  
-   [Utilisation des sources de données](../../odbc/reference/using-data-sources.md)  
  
-   [Exemple de source de données](../../odbc/reference/data-source-example.md)
