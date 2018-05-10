---
title: Microsoft SQL et les exigences du RGPD | Microsoft Docs
ms.custom: ''
ms.date: 05/24/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: security
ms.tgt_pltfrm: ''
ms.topic: conceptual
caps.latest.revision: 2
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: '>= aps-pdw-2016 || = azuresqldb-current || = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: e5144b4ec829f57b77ae92fb3d55a724bb08964b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="guide-to-enhancing-privacy-and-addressing-gdpr-requirements-with-the-microsoft-sql-platform"></a>Guide d’amélioration de la confidentialité et du traitement des exigences du RGPD avec la plateforme Microsoft SQL
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

## <a name="summary"></a>Résumé
Le 25 mai 2018, une loi européenne sur la confidentialité des données va entrer en vigueur. Elle doit fixer une nouvelle norme globale pour la protection, la sécurité et le respect des données personnelles. Le RGPD (Règlement Général sur la Protection des Données) renforce la protection des droits et le respect de la vie privée des individus. Il établit des exigences de confidentialité strictes et globales qui régissent la façon dont les données personnelles sont gérées et protégées, en accord avec le respect des choix individuels. 

Les clients Microsoft SQL soumis au RGPD, que ce soit pour la gestion des bases de données cloud ou locales, ou les deux, doivent veiller à ce que les données de qualification dans leurs systèmes de base de données soient gérées et protégées de manière appropriée, conformément aux principes du RGPD. En d’autres termes, de nombreux clients doivent revoir ou modifier leurs procédures de gestion des bases de données et de traitement des données, en se concentrant sur la sécurité du traitement des données tel que cela est stipulé dans le RGPD.

Les technologies Microsoft SQL offrent de nombreuses fonctionnalités de sécurité intégrées qui permettent de réduire les risques liés aux données, mais également d’améliorer la protection et la gestion des données au niveau de la base de données, et au-delà. Cet article examine ces fonctionnalités et partage certaines approches utilisées par Microsoft avec Microsoft SQL pour atteindre les objectifs de protection des données fixés par le RGPD.
   
  
**Rédacteur :** Ronit Reger

**Réviseurs techniques :** Conor Cunningham ; Joachim Hammer ; Shai Kariv ; Julie Koesmarno ; Alice Kupcik ; Ron Matchoro ; Gilad Mittelman ; Dan Rediske ; Tomer Weisberg 
  
**Date de publication :** mai 2017  
  
**S’applique à :** SQL Server (toutes les versions), Azure SQL Database, Azure SQL Data Warehouse, Analytics Platform System 
  
Pour passer en revue ce document, téléchargez le [Guide d’amélioration de la confidentialité et du traitement des exigences du RGPD avec la plateforme Microsoft SQL](http://download.microsoft.com/download/4/9/4/4948194B-A613-49ED-90A5-5144313549AB/microsoft-sql-and-the-gdpr.pdf).   
