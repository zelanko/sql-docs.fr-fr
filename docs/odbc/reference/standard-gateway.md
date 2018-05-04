---
title: Passerelle standard | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], gateways
- standard gateways [ODBC]
- gateways [ODBC]
ms.assetid: b8341492-2141-4bab-80bd-f2752223079e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e1e75f97ded8f999d5fa945e0aafb04322d51540
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="standard-gateway"></a>Passerelle standard
A *passerelle* est un logiciel qui provoque un SGBD ressemble à un autre. Autrement dit, la passerelle accepte l’interface de programmation, la grammaire SQL, protocole d’un SGBD unique de flux de données et le traduit pour l’interface de programmation, grammaire SQL, et le protocole du SGBD masqué de flux de données. Par exemple, les applications écrites pour utiliser Microsoft® SQL Server™ peuvent également accéder aux données DB2 via la passerelle de DB2 Decisionware Micro ; Ce produit entraîne DB2 ressemble à SQL Server. Lorsque les passerelles sont utilisées, une autre passerelle doit être écrites pour chaque base de données cible.  
  
 Bien que les passerelles sont limités par des différences d’architecture entre SGBD, ils sont un bon candidat pour la normalisation. Toutefois, si tous les SGBD doivent normaliser sur l’interface de programmation, grammaire SQL et les données de protocole de flux d’un SGBD unique, dont SGBD doit être choisi comme la norme ? Certainement aucun fournisseur SGBD commercial n’est susceptible de normaliser sur un produit concurrent. Et si une interface de programmation standard, la grammaire SQL et le protocole de flux de données sont développées, aucune passerelle n’est nécessaire.
