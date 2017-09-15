---
title: Passerelle standard | Documents Microsoft
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
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
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 9375bc6bf5054bdfeddd4fc5e53a1494d74eb88b
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="standard-gateway"></a>Passerelle standard
A *passerelle* est un logiciel qui provoque un SGBD ressemble à un autre. Autrement dit, la passerelle accepte l’interface de programmation, la grammaire SQL, protocole d’un SGBD unique de flux de données et le traduit pour l’interface de programmation, grammaire SQL, et le protocole du SGBD masqué de flux de données. Par exemple, les applications écrites pour utiliser Microsoft® SQL Server™ peuvent également accéder aux données DB2 via la passerelle de DB2 Decisionware Micro ; Ce produit entraîne DB2 ressemble à SQL Server. Lorsque les passerelles sont utilisées, une autre passerelle doit être écrites pour chaque base de données cible.  
  
 Bien que les passerelles sont limités par des différences d’architecture entre SGBD, ils sont un bon candidat pour la normalisation. Toutefois, si tous les SGBD doivent normaliser sur l’interface de programmation, grammaire SQL et les données de protocole de flux d’un SGBD unique, dont SGBD doit être choisi comme la norme ? Certainement aucun fournisseur SGBD commercial n’est susceptible de normaliser sur un produit concurrent. Et si une interface de programmation standard, la grammaire SQL et le protocole de flux de données sont développées, aucune passerelle n’est nécessaire.
