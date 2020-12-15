---
description: Présentation du verrouillage de ligne
title: Présentation du verrouillage de ligne | Microsoft Docs
ms.custom: ''
ms.date: 12/08/2020
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 63c76a2f-f2b9-461f-8904-acbda0169ac3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e5305f3feaa80d0a83dd1e7bfd97088492608ae5
ms.sourcegitcommit: 7f76975c29d948a9a3b51abce564b9c73d05dcf0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2020
ms.locfileid: "96901057"
---
# <a name="understanding-row-locking"></a>Présentation du verrouillage de ligne

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

Le [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] utilise des verrous de ligne [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Ces verrous implémentent les contrôles de concurrence entre plusieurs utilisateurs qui effectuent simultanément des modifications dans une base de données. Par défaut, les transactions et verrous sont gérés sur la base de chaque connexion. Par exemple, si une application ouvre deux connexions JDBC, les verrous acquis par une connexion ne peuvent pas être partagés avec l'autre connexion. Aucune connexion ne peut acquérir des verrous qui seraient en conflit avec les verrous détenus par l'autre connexion.

> [!NOTE]  
> Si le verrouillage de ligne est utilisé, toutes les lignes dans la mémoire tampon d'extraction sont verrouillées ; par conséquent, un très grand paramètre pour la taille d'extraction peut affecter la concurrence.

Le verrouillage est utilisé pour garantir l'intégrité transactionnelle et la cohérence de base de données. Le verrouillage empêche les utilisateurs de lire des données qui sont en cours de modification par d'autres utilisateurs et empêche plusieurs utilisateurs de modifier simultanément les mêmes données. Si le verrouillage n'est pas utilisé, les données dans la base de données peuvent devenir logiquement incorrectes et les requêtes exécutées contre ces données peuvent produire des résultats inattendus.

> [!NOTE]  
> Pour plus d’informations sur le verrouillage de ligne dans [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], consultez [« Verrouillage dans [!INCLUDE[ssDE](../../includes/ssde_md.md)] »](../../relational-databases/sql-server-transaction-locking-and-row-versioning-guide.md#Lock_Engine) dans la documentation en ligne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].

## <a name="see-also"></a>Voir aussi

[Gestion des jeux de résultats avec le pilote JDBC](../../connect/jdbc/managing-result-sets-with-the-jdbc-driver.md)
