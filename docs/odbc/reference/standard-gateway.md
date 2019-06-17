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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: c70a558b065765dd9f8c0895345959e8aa22ebfe
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "63232094"
---
# <a name="standard-gateway"></a>Passerelle standard
Un *passerelle* est un logiciel qui provoque un SGBD ressemble à un autre. Autrement dit, la passerelle accepte l’interface de programmation, la syntaxe SQL et protocole de SGBD unique de flux de données et le traduit à l’interface de programmation, grammaire SQL, et protocole du SGBD masqué de flux de données. Par exemple, les applications écrites pour utiliser Microsoft® SQL Server™ peuvent également accéder à des données de DB2 via la passerelle de DB2 Decisionware Micro ; Ce produit entraîne DB2 ressemble à SQL Server. Lorsque les passerelles sont utilisés, une autre passerelle doit être écrites pour chaque base de données cible.  
  
 Bien que les passerelles sont limités par les différences architecturales entre le SGBD, ils sont un bon candidat pour la normalisation. Toutefois, si tous les SGBD sont à une standardisation sur l’interface de programmation, grammaire SQL et protocole data stream de SGBD unique dont SGBD doit être choisi comme la norme ? Aucun fournisseur de SGBD commerciale n’est certainement susceptible de normaliser sur un produit concurrent. Et si une interface de programmation standard, la grammaire SQL et le protocole de flux de données sont développés, aucune passerelle n’est nécessaire.
