---
title: Installation des composants ODBC | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC]
- installing ODBC components [ODBC], about installing
- ODBC [ODBC], component installation
ms.assetid: b7e48e9c-8912-4003-b4ef-30aa44de06a7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: bf2ef856d8970bf60b3f1f329c57a2379eb528dc
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094026"
---
# <a name="installing-odbc-components"></a>Installation des composants ODBC
> [!NOTE]  
>  ODBC à partir de Windows XP et Windows Server 2003, est inclus dans le système d’exploitation Windows. Vous devez explicitement uniquement installer ODBC dans les versions antérieures de Windows.  
  
 Cette section décrit comment les composants ODBC sont installées et supprimées. Étant donné que les développeurs de pilotes toujours installer un composant ODBC (leurs pilotes), dont ils ont besoin de lire cette section. Les développeurs d’applications doivent lire cette section uniquement si ils proposent des composants ODBC avec leurs applications. Composants ODBC incluent le Gestionnaire de pilotes, pilotes, traducteurs, le programme d’installation DLL, la bibliothèque de curseurs et les fichiers associés. Dans le cadre de cette section, les applications ODBC ne sont pas considérés comme des composants ODBC.  
  
> [!NOTE]  
>  Cette section est spécifique aux plateformes de Microsoft Windows. Comment les composants ODBC sont installés sur d’autres plates-formes sont spécifique à la plateforme.  
  
 Composants ODBC sont installées et supprimées sur une base de composant par composant, pas une base de fichier par fichier. Par exemple, si un traducteur compose du traducteur lui-même et un nombre de fichiers de données, ces fichiers sont installés et supprimés en tant que groupe ; non, ils doivent être installés et supprimés sur une base de fichier par fichier. La raison à cela consiste à s’assurer que les composants complets uniquement existent sur le système.  
  
 Dans le cadre de l’installation et la suppression de composants, les éléments suivants sont définis comme des composants ODBC :  
  
-   **Composants principaux.** Le Gestionnaire de pilotes, la bibliothèque de curseurs, la DLL d’installation et n’importe quel autre liés fichiers constituent les principaux composants et doivent être installés et supprimés en tant que groupe.  
  
-   **Pilotes.** Chaque pilote est un composant distinct.  
  
-   **Traducteurs.** Chaque traduction est un composant distinct.  
  
 Avec la prise en charge d’Unicode dans ODBC 3.5 et versions ultérieures, une attention doit être accordée à l’aide de composants OLE DB avec ODBC. La version 1.1 du fournisseur OLE DB pour ODBC a été écrite dans les spécifications Unicode spécifiques dans ODBC 3.0. Étant donné que ces spécifications sont modifiées dans ODBC 3.5, il est nécessaire d’avoir la version 1.5 ou version ultérieure du fournisseur lors de l’utilisation d’ODBC 3.5 et versions ultérieures. Cette section contient les rubriques suivantes.  
  
-   [Composants d’installation](../../../odbc/reference/install/installation-components.md)  
  
-   [Nombre d’utilisations](../../../odbc/reference/install/usage-counting.md)
