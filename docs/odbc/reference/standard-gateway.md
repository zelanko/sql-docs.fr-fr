---
title: Passerelle standard (fr) Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81280072"
---
# <a name="standard-gateway"></a>Passerelle standard
Une *passerelle* est un logiciel qui fait ressembler un DBMS à un autre. Autrement dit, la passerelle accepte l’interface de programmation, la grammaire SQL, et le protocole de flux de données d’un seul DBMS et le traduit à l’interface de programmation, la grammaire SQL, et le protocole de flux de données de la DBMS cachée. Par exemple, les applications écrites pour utiliser Microsoft® SQL Server™ peuvent également accéder aux données DB2 via la passerelle Micro Decisionware DB2; ce produit provoque DB2 à ressembler à SQL Server. Lorsque des passerelles sont utilisées, une passerelle différente doit être écrite pour chaque base de données cible.  
  
 Bien que les passerelles soient limitées par les différences architecturales entre les DBMS, elles sont un bon candidat à la normalisation. Toutefois, si tous les DBMS doivent être normalisés sur l’interface de programmation, la grammaire SQL et le protocole de flux de données d’un seul DBMS, dont le DBMS doit être choisi comme norme? Il est certain qu’aucun fournisseur commercial DBMS n’est susceptible d’accepter de normaliser le produit d’un concurrent. Et si une interface de programmation standard, la grammaire SQL et le protocole de flux de données sont développés, aucune passerelle n’est nécessaire.
