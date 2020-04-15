---
title: Support transactionnel (fr) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- transactions [ODBC], degree of support
ms.assetid: d56e1458-8da2-4d73-a777-09e045c30a33
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a5b9d731d12329a4ef663b1ea66cdc59a0b153fa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81297977"
---
# <a name="transaction-support"></a>Prise en charge des transactions
Le degré de prise en charge des transactions est défini par le conducteur. ODBC est conçu pour être implémenté sur une base de données d’utilisateur ou de bureau unique qui n’a pas besoin de gérer plusieurs mises à jour de ses données. De plus, certaines bases de données qui prennent en charge les transactions ne le font que pour les énoncés de LANGAGE de manipulation de données (DML) de SQL; il existe des restrictions ou des sémantiques spéciales concernant l’utilisation du langage de définition des données (DDL) lorsqu’une transaction est active. Autrement dit, il peut y avoir un support transactionnel pour plusieurs mises à jour simultanées des tableaux, mais pas pour changer le nombre et la définition des tableaux au cours d’une transaction.  
  
 Une demande détermine si les transactions sont prises en charge, si DDL peut être inclus dans une transaction, et tout effet spécial d’inclure DDL dans une transaction, en appelant **SQLGetInfo** avec l’option SQL_TXN_CAPABLE. Pour plus d’informations, consultez la description de la fonction [SQLGetInfo.](../../../odbc/reference/syntax/sqlgetinfo-function.md)  
  
 Si le conducteur ne prend pas en charge les transactions, mais que l’application a la capacité (à l’aide d’une API autre qu’ODBC) de verrouiller et de déverrouiller des données, les applications peuvent obtenir un support transactionnel en verrouillant et en déverrouillant des dossiers et des tableaux au besoin. Pour mettre en œuvre l’exemple de transfert de compte, l’application verrouillerait les dossiers des deux comptes, copierait les valeurs actuelles, débiterait le premier compte, créditerait le deuxième compte et déverrouillerait les dossiers. En cas d’échec des étapes, l’application réinitialiserait les comptes à l’aide des copies.  
  
 Même les sources de données qui prennent en charge les transactions pourraient ne pas être en mesure de prendre en charge plus d’une transaction à la fois dans un environnement particulier. Les applications appellent **SQLGetInfo** avec l’option SQL_MULTIPLE_ACTIVE_TXN pour déterminer si une source de données peut prendre en charge les transactions actives simultanées sur plus d’une connexion dans le même environnement. Étant donné qu’il y a une transaction par connexion, cela n’est intéressant que pour les applications qui ont plusieurs connexions à la même source de données.
