---
title: Compatibilité des versions | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- table-valued parameters (ODBC), cross-version compatibility
ms.assetid: 5f14850b-b85c-41e2-8116-6f5b3f5e0856
caps.latest.revision: 14
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d256fe042562f902aeb3e6229b36f25308e3c138
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042211"
---
# <a name="cross-version-compatibility"></a>Compatibilité des versions
  Les conflits de version peuvent se produire lorsque les instances client ou serveur de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] sont censées traiter les paramètres table.  
  
 En général, les fonctionnalités des paramètres table ne sont accessibles qu'aux clients [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (avec SQL Server Native Client 10.0) ou version ultérieure connectés aux serveurs [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou version ultérieure). Nouvelles colonnes dans les jeux de résultats de fonction de catalogue ne sont présentes lorsqu’il est connecté à un [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (ou version ultérieure) server.  
  
 Si une application cliente compilée avec une version antérieure de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client exécute des instructions qui attendent des paramètres table, le serveur détecte cette situation via une erreur de conversion de données, et ODBC retourne celle-ci comme SQLSTATE 07006, avec le message « Violation de l'attribut de type de données restreint ».  
  
 Si une application cliente qui a été compilée avec [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client 10.0 ou version ultérieure tente d’utiliser des paramètres table lorsqu’il est connecté à une instance de serveur antérieure à [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)], [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client détecte et SQLBindCol, Appels SQLBindParameter, SQLSetDescFields et SQLSetDescRec échoue avec SQLSTATE 07006 et le message « Restricted violation d’attribut de type de données (la version de SQL Server pour cette connexion ne prend pas en charge les paramètres table) ».  
  
## <a name="see-also"></a>Voir aussi  
 [Paramètres table &#40;ODBC&#41;](table-valued-parameters-odbc.md)  
  
  