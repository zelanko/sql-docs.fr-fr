---
title: Pilotes basés sur DBMS (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4e7b7b153d0b0cb0a3e6a3d738908b0039b95679
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306485"
---
# <a name="dbms-based-drivers"></a>Pilotes basés sur le SGDB
Les pilotes basés sur DBMS sont utilisés avec des sources de données telles qu’Oracle ou SQL Server qui fournissent un moteur de base de données autonome pour le conducteur à utiliser. Ces conducteurs accèdent aux données physiques par l’intermédiaire du moteur autonome; c’est-à-dire qu’ils soumettent des relevés SQL et récupèrent les résultats du moteur.  
  
 Étant donné que les pilotes basés sur DBMS utilisent un moteur de base de données existant, ils sont généralement plus faciles à écrire que les pilotes basés sur des fichiers. Bien qu’un conducteur basé sur DBMS puisse être facilement mis en œuvre en traduisant les appels ODBC vers des appels API natifs, cela se traduit par un conducteur plus lent. Une meilleure façon de mettre en œuvre un pilote basé sur DBMS est d’utiliser le protocole de flux de données sous-jacent, qui est généralement ce que fait l’API indigène. Par exemple, un conducteur de serveur SQL devrait utiliser TDS (le protocole de flux de données pour SQL Server) plutôt que DB Library (l’API native pour SQL Server). Une exception à cette règle est lorsque ODBC est l’API indigène. Par exemple, Watcom SQL est un moteur autonome qui réside sur la même machine que l’application et est chargé directement comme le conducteur.  
  
 Les pilotes basés sur DBMS agissent comme le client dans une configuration client/serveur où la source de données agit comme serveur. Dans la plupart des cas, le client (pilote) et le serveur (source de données) résident sur différentes machines, bien que les deux puissent résider sur la même machine en cours d’exécution d’un système d’exploitation multitâche. Une troisième possibilité est une *passerelle,* qui se trouve entre le conducteur et la source de données. Une passerelle est un logiciel qui fait ressembler un DBMS à un autre. Par exemple, les applications écrites pour utiliser SQL Server peuvent également accéder aux données DB2 via la passerelle Micro Decisionware DB2; ce produit provoque DB2 à ressembler à SQL Server.  
  
 L’illustration suivante montre trois configurations différentes de pilotes basés sur DBMS. Dans la première configuration, le conducteur et la source de données résident sur la même machine. Dans la seconde, le conducteur et la source de données résident sur différentes machines. Dans la troisième, le conducteur et la source de données résident sur différentes machines et une passerelle se trouve entre eux, résidant sur une autre machine.  
  
 ![Trois configurations pour les pilotes DBMS&#45;basés](../../odbc/reference/media/pr07.gif "pr07")
