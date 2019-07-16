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
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68111250"
---
# <a name="dbms-based-drivers"></a>Pilotes basés sur le SGDB
Pilotes basés sur SGBD sont utilisées avec des sources de données telles que Oracle ou SQL Server qui fournissent un moteur de base de données autonome pour le pilote à utiliser. Ces pilotes accéder aux données physiques via le moteur autonome ; Autrement dit, ils soumettez les instructions SQL à et récupérer les résultats à partir du moteur.  
  
 Étant donné que les pilotes basés sur SGBD utilisent un moteur de base de données existant, ils sont généralement plus faciles à écrire que les pilotes basés sur le fichier. Bien qu’un pilote de SGBD peut facilement être implémenté en traduisant les appels à des appels d’API ODBC, cela entraîne un pilote plus lent. Une meilleure façon d’implémenter un pilote de SGBD consiste à utiliser le protocole de flux de données sous-jacent, ce que fait généralement l’API native. Par exemple, un pilote de SQL Server doit utiliser TDS (le protocole data stream pour SQL Server) au lieu de la bibliothèque de base de données (l’API native pour SQL Server). Une exception à cette règle est lorsqu’ODBC est l’API native. Par exemple, Watcom SQL est un moteur autonome qui réside sur le même ordinateur que l’application et est chargé directement avec le pilote.  
  
 Pilotes basés sur SGBD agissent en tant que le client dans une configuration de client/serveur où la source de données joue le rôle de serveur. Dans la plupart des cas, le client (pilote) et le serveur (source de données) se trouvent sur des ordinateurs différents, bien que les deux peut se trouver sur le même ordinateur exécutant un système d’exploitation multitâche. Une troisième possibilité est un *passerelle,* qui se trouve entre le pilote et de la source de données. Une passerelle est un logiciel qui provoque un SGBD ressemble à un autre. Par exemple, les applications écrites pour utiliser SQL Server peuvent également accéder à des données de DB2 via la passerelle de DB2 Decisionware Micro ; Ce produit entraîne DB2 ressemble à SQL Server.  
  
 L’illustration suivante montre trois différentes configurations de pilotes basés sur SGBD. Dans la première configuration, le pilote et la source de données résident sur le même ordinateur. Dans la seconde, le pilote et la source de données résident sur des ordinateurs différents. Dans la troisième, le pilote et la source de données résident sur des ordinateurs différents, et une passerelle se trouve entre eux, résidant sur un autre ordinateur.  
  
 ![Trois configurations de SGBD&#45;pilotes](../../odbc/reference/media/pr07.gif "pr07")
