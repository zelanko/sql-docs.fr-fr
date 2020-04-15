---
title: Qu’est-ce que ODBC ? | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], about ODBC
ms.assetid: badf3a45-f941-44ae-a31d-393116f68a18
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ea0aa81188e5e58d3a66032af38700ece2d4e5b4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81286499"
---
# <a name="what-is-odbc"></a>Qu’est-ce que ODBC ?
Beaucoup d’idées fausses sur ODBC existent dans le monde de l’informatique. Pour l’utilisateur final, il s’agit d’une icône dans le panneau de contrôle Microsoft® Windows®. Pour le programmeur d’applications, il s’agit d’une bibliothèque contenant des routines d’accès aux données. Pour beaucoup d’autres, c’est la réponse à tous les problèmes d’accès aux bases de données jamais imaginés.  
  
 D’abord et avant tout, ODBC est une spécification pour une API de base de données. Cette API est indépendante de n’importe quel DBMS ou système d’exploitation; bien que ce manuel utilise C, l’API ODBC est indépendante de la langue. L’API ODBC est basée sur les spécifications CLI de Open Group et ISO/IEC. ODBC 3. *x* implémente pleinement ces deux spécifications - les versions antérieures d’ODBC étaient basées sur des versions préliminaires de ces spécifications, mais ne les implémentaient pas entièrement - et ajoute les fonctionnalités couramment nécessaires par les développeurs d’applications de base de données basées sur l’écran, telles que les curseurs défilementables.  
  
 Les fonctions de l’API ODBC sont mises en œuvre par les développeurs de pilotes spécifiques à DBMS. Les applications appellent les fonctions de ces pilotes pour accéder aux données d’une manière indépendante DBMS. Un Driver Manager gère la communication entre les applications et les conducteurs.  
  
 Bien que Microsoft fournit un gestionnaire de pilote pour les ordinateurs exécutant Microsoft Windows® 95 et plus tard, a écrit plusieurs pilotes ODBC, et appelle les fonctions ODBC de certaines de ses applications, n’importe qui peut écrire des applications ODBC et des pilotes. En fait, la grande majorité des applications ODBC et les pilotes disponibles aujourd’hui sont écrits par des entreprises autres que Microsoft. En outre, les pilotes et applications ODBC existent sur le Macintosh® et une variété de plates-formes UNIX.  
  
 Pour aider les développeurs d’applications et de pilotes, Microsoft offre un kit de développement logiciel ODBC (SDK) pour les ordinateurs fonctionnant sous Windows 95 et plus tard qui fournit le gestionnaire de pilote, installateur DLL, outils de test et des applications d’échantillons. Microsoft a fait équipe avec Visigenic Software pour porter ces SDK au Macintosh et une variété de plates-formes UNIX.  
  
 Il est important de comprendre que L’ODBC est conçu pour exposer les capacités de base de données, et non pour les compléter. Ainsi, les auteurs d’applications ne doivent pas s’attendre à ce que l’utilisation d’ODBC transforme soudainement une simple base de données en un moteur de base de données relationnel entièrement en vedette. Les auteurs de pilotes ne sont pas non plus censés implémenter des fonctionnalités que l’on ne trouve pas dans la base de données sous-jacente. Une exception à cela est que les développeurs qui écrivent des pilotes qui accèdent directement aux données de fichiers (comme les données dans un fichier Xbase) sont tenus d’écrire un moteur de base de données qui prend en charge au moins une fonctionnalité SQL minimale. Une autre exception est que le composant ODBC du SDK Windows, anciennement inclus dans le SDK Microsoft Data Access Components (MDAC), fournit une bibliothèque de curseurs qui simule des curseurs défilants pour les conducteurs qui implémentent un certain niveau de fonctionnalité.  
  
 Les applications qui utilisent ODBC sont responsables de toutes les fonctionnalités de base de données croisées. Par exemple, ODBC n’est pas un moteur de jointure hétérogène, ni un processeur de transaction distribué. Cependant, parce qu’il est DBMS-indépendant, il peut être utilisé pour construire de tels outils de base de données croisées.
