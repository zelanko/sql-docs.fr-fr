---
title: Prise en charge des transactions | Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81297977"
---
# <a name="transaction-support"></a>Prise en charge des transactions
Le niveau de prise en charge des transactions est défini par le pilote. ODBC est conçu pour être implémenté sur une base de données de bureau ou d’utilisateur unique qui n’a pas besoin de gérer plusieurs mises à jour de ses données. En outre, certaines bases de données qui prennent en charge les transactions ne le font que pour les instructions DML (Data Manipulation Language) de SQL ; Il existe des restrictions ou une sémantique de transaction spéciale en ce qui concerne l’utilisation du langage de définition de données (DDL) lorsqu’une transaction est active. Autrement dit, il peut y avoir une prise en charge des transactions pour plusieurs mises à jour simultanées des tables, mais pas pour modifier le nombre et la définition des tables au cours d’une transaction.  
  
 Une application détermine si les transactions sont prises en charge, si DDL peut être inclus dans une transaction, et tous les effets spéciaux de l’inclusion de DDL dans une transaction, en appelant **SQLGetInfo** avec l’option SQL_TXN_CAPABLE. Pour plus d’informations, consultez la description de la fonction [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md) .  
  
 Si le pilote ne prend pas en charge les transactions, mais que l’application a la possibilité (à l’aide d’une API autre qu’ODBC) de verrouiller et de déverrouiller les données, les applications peuvent prendre en charge la transaction en verrouillant et déverrouillant les enregistrements et les tables en fonction des besoins. Pour implémenter l’exemple de transfert de compte, l’application verrouille les enregistrements pour les deux comptes, copie les valeurs actuelles, débite le premier compte, crédite le deuxième compte et déverrouille les enregistrements. En cas d’échec d’une étape, l’application réinitialise les comptes à l’aide des copies.  
  
 Même les sources de données qui prennent en charge les transactions peuvent ne pas être en mesure de prendre en charge plusieurs transactions à la fois dans un environnement particulier. Les applications appellent **SQLGetInfo** avec l’option SQL_MULTIPLE_ACTIVE_TXN pour déterminer si une source de données peut prendre en charge des transactions actives simultanées sur plusieurs connexions dans le même environnement. Étant donné qu’il y a une transaction par connexion, cela n’est intéressant que pour les applications qui ont plusieurs connexions à la même source de données.
