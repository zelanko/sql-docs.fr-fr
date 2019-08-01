---
ms.openlocfilehash: 327fd6bac9bc1036a0dd07f7b955ee92cb7e40c8
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68223538"
---
  Avec l'arrivée de SQL Server 2005, le comportement des schémas a changé. Ainsi, le code qui suppose que les schémas sont équivalents aux utilisateurs de base de données peut ne plus renvoyer des résultats corrects. Vous ne devez pas utiliser d’anciens affichages catalogue, notamment sysobjects, dans une base de données où l’une des instructions DDL suivantes a été utilisée : CREATE SCHEMA, ALTER SCHEMA, DROP SCHEMA, CREATE USER, ALTER USER, DROP USER, CREATE ROLE, ALTER ROLE, DROP ROLE, CREATE APPROLE, ALTER APPROLE, DROP APPROLE, ALTER AUTHORIZATION. Dans ces bases de données, vous devez utiliser les nouveaux affichages catalogue. Les nouveaux affichages catalogue tiennent compte de la séparation des principaux et des schémas introduite dans SQL Server 2005 Pour plus d’informations sur les affichages catalogue, consultez [Affichages catalogue &#40;Transact-SQL&#41;](../relational-databases/system-catalog-views/catalog-views-transact-sql.md).
   