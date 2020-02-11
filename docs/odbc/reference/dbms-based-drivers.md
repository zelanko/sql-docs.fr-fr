---
title: Pilotes basés sur SGBD | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- drivers [ODBC], DBMS-based drivers
- DBMS-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
ms.assetid: e2208ee0-4cd6-4f0d-bb71-a0b54f7d9330
author: MightyPen
ms.author: genemi
ms.openlocfilehash: fcd2221d9a0bb9cba42745901e5f00a6f8c8415e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68111250"
---
# <a name="dbms-based-drivers"></a>Pilotes basés sur le SGDB
Les pilotes basés sur SGBD sont utilisés avec des sources de données telles qu’Oracle ou SQL Server qui fournissent un moteur de base de données autonome pour le pilote à utiliser. Ces pilotes accèdent aux données physiques via le moteur autonome. autrement dit, ils envoient des instructions SQL à et récupèrent les résultats du moteur.  
  
 Étant donné que les pilotes basés sur SGBD utilisent un moteur de base de données existant, ils sont généralement plus faciles à écrire que les pilotes basés sur des fichiers. Même s’il est facile d’implémenter un pilote SGBD en traduisant des appels ODBC à des appels d’API natifs, cela entraîne un pilote plus lent. Une meilleure façon d’implémenter un pilote basé sur un SGBD consiste à utiliser le protocole de flux de données sous-jacent, qui est généralement ce que fait l’API native. Par exemple, un pilote de SQL Server doit utiliser TDS (le protocole de flux de données pour SQL Server) au lieu de la bibliothèque de base de données (API native pour SQL Server). Une exception à cette règle est quand ODBC est l’API native. Par exemple, Watcom SQL est un moteur autonome qui réside sur le même ordinateur que l’application et qui est chargé directement comme pilote.  
  
 Les pilotes basés sur SGBD jouent le rôle de client dans une configuration client/serveur où la source de données agit en tant que serveur. Dans la plupart des cas, le client (pilote) et le serveur (source de données) résident sur des ordinateurs différents, même si les deux peuvent résider sur le même ordinateur exécutant un système d’exploitation multitâche. Une troisième possibilité est une *passerelle,* qui se situe entre le pilote et la source de données. Une passerelle est un élément logiciel qui fait qu’un SGBD ressemble à un autre SGBD. Par exemple, les applications écrites pour utiliser SQL Server peuvent également accéder aux données DB2 par le biais de la passerelle DB2 de micro-décision. ce produit a pour effet que DB2 ressemble à SQL Server.  
  
 L’illustration suivante montre trois configurations différentes de pilotes basés sur des SGBD. Dans la première configuration, le pilote et la source de données résident sur le même ordinateur. Dans le deuxième cas, le pilote et la source de données résident sur des ordinateurs différents. Dans le troisième cas, le pilote et la source de données résident sur des ordinateurs différents et une passerelle se trouve entre eux, résidant sur un autre ordinateur.  
  
 ![Trois configurations pour les pilotes basés sur&#45;SGBD](../../odbc/reference/media/pr07.gif "pr07")
