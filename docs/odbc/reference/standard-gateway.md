---
title: Passerelle standard | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], gateways
- standard gateways [ODBC]
- gateways [ODBC]
ms.assetid: b8341492-2141-4bab-80bd-f2752223079e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 67551845c0dd8c6a28c0c4bc1c50f54ee8232df1
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280072"
---
# <a name="standard-gateway"></a>Passerelle standard
Une *passerelle* est un élément logiciel qui fait qu’un SGBD ressemble à un autre SGBD. Autrement dit, la passerelle accepte l’interface de programmation, la grammaire SQL et le protocole de flux de données d’un seul SGBD et la convertit en l’interface de programmation, la grammaire SQL et le protocole de flux de données du SGBD masqué. Par exemple, les applications écrites pour utiliser Microsoft® SQL Server™ peuvent également accéder aux données DB2 par le biais de la passerelle DB2 de micro-décision. ce produit a pour effet que DB2 ressemble à SQL Server. Lorsque les passerelles sont utilisées, une autre passerelle doit être écrite pour chaque base de données cible.  
  
 Bien que les passerelles soient limitées par les différences architecturales entre les SGBD, elles sont un bon candidat à la normalisation. Toutefois, si tous les SGBD doivent se normaliser sur l’interface de programmation, la grammaire SQL et le protocole de flux de données d’un SGBD unique, dont le SGBD est choisi comme standard ? Certainement, aucun fournisseur de SGBD commercial n’est susceptible d’accepter de standardiser le produit d’un concurrent. Et si une interface de programmation standard, une grammaire SQL et un protocole de flux de données sont développés, aucune passerelle n’est nécessaire.
