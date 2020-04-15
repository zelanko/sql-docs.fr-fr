---
title: Installation de composants ODBC (fr) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbd0a6aeba8073ce14b08b8635396b1f231895fb
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298979"
---
# <a name="installing-odbc-components"></a>Installation des composants ODBC
> [!NOTE]  
>  En commençant par Windows XP et Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous ne devez installer explicitement ODBC que sur les versions antérieures de Windows.  
  
 Cette section décrit comment les composants ODBC sont installés et enlevés. Étant donné que les développeurs de pilotes installent toujours un composant ODBC (leur conducteur), ils doivent lire cette section. Les développeurs d’applications n’ont besoin de lire cette section que s’ils expédient des composants ODBC avec leurs applications. Les composants ODBC comprennent le Driver Manager, les chauffeurs, les traducteurs, l’installateur DLL, la bibliothèque de curseurs et tous les fichiers connexes. Aux fins de la présente section, les demandes d’ODBC ne sont pas considérées comme des composantes de l’ODBC.  
  
> [!NOTE]  
>  Cette section est spécifique aux plates-formes Microsoft Windows. La façon dont les composants ODBC sont installés sur d’autres plates-formes est spécifique à la plate-forme.  
  
 Les composants ODBC sont installés et supprimés composant par composant, et non sur une base de fichier par fichier. Par exemple, si un traducteur se compose du traducteur lui-même et d’un certain nombre de fichiers de données, ces fichiers sont installés et supprimés en tant que groupe; ils ne doivent pas être installés et supprimés au fichier par fichier. La raison en est de s’assurer que seuls des composants complets existent sur le système.  
  
 Aux fins de l’installation et de l’élimination des composants, les éléments suivants sont définis comme étant des composants ODBC :  
  
-   **Composants de base.** Le Driver Manager, la bibliothèque de curseurs, l’installateur DLL et tous les autres fichiers connexes constituent les composants de base et doivent être installés et retirés en groupe.  
  
-   **Pilotes.** Chaque conducteur est un composant distinct.  
  
-   **Traducteurs.** Chaque traducteur est un composant distinct.  
  
 Avec l’appui d’Unicode dans ODBC 3.5 et plus tard, une certaine considération doit être accordée à l’utilisation de composants OLE DB avec ODBC. La version 1.1 du fournisseur OLE DB pour ODBC a été écrite selon des spécifications Unicode spécifiques au sein d’ODBC 3.0. Étant donné que ces spécifications ont changé dans ODBC 3.5, il est nécessaire d’avoir la version 1.5 ou plus tard du fournisseur lors de l’utilisation oDBC 3.5 et plus tard. Cette section contient les rubriques suivantes :  
  
-   [Composants d’installation](../../../odbc/reference/install/installation-components.md)  
  
-   [Nombre d’utilisations](../../../odbc/reference/install/usage-counting.md)
