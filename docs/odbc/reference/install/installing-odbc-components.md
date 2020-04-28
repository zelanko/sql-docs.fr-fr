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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: bbd0a6aeba8073ce14b08b8635396b1f231895fb
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81298979"
---
# <a name="installing-odbc-components"></a>Installation des composants ODBC
> [!NOTE]  
>  À compter de Windows XP et de Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous devez uniquement installer explicitement ODBC sur les versions antérieures de Windows.  
  
 Cette section décrit comment installer et supprimer des composants ODBC. Étant donné que les développeurs de pilotes installent toujours un composant ODBC (leur pilote), ils doivent lire cette section. Les développeurs d’applications doivent lire cette section uniquement s’ils expédient des composants ODBC avec leurs applications. Les composants ODBC incluent le gestionnaire de pilotes, les pilotes, les traducteurs, la DLL du programme d’installation, la bibliothèque de curseurs et tous les fichiers associés. Dans le cadre de cette section, les applications ODBC ne sont pas considérées comme des composants ODBC.  
  
> [!NOTE]  
>  Cette section est spécifique aux plates-formes Microsoft Windows. La façon dont les composants ODBC sont installés sur d’autres plateformes est spécifique à la plateforme.  
  
 Les composants ODBC sont installés et supprimés sur une base composant par composant, et non fichier par fichier. Par exemple, si un traducteur se compose du traducteur lui-même et d’un certain nombre de fichiers de données, ces fichiers sont installés et supprimés en tant que groupe. elles ne doivent pas être installées et supprimées fichier par fichier. Cela a pour but de s’assurer que seuls les composants complets existent sur le système.  
  
 Dans le cadre de l’installation et de la suppression de composants, les éléments suivants sont définis comme étant des composants ODBC :  
  
-   **Composants principaux.** Le gestionnaire de pilotes, la bibliothèque de curseurs, la DLL du programme d’installation et tous les autres fichiers associés composent les composants principaux et doivent être installés et supprimés en tant que groupe.  
  
-   **Stratégiques.** Chaque pilote est un composant distinct.  
  
-   **Traducteurs.** Chaque traducteur est un composant distinct.  
  
 Avec la prise en charge d’Unicode dans ODBC 3,5 et versions ultérieures, vous devez tenir compte de l’utilisation de OLE DB composants avec ODBC. La version 1,1 du fournisseur OLE DB pour ODBC a été écrite dans des spécifications Unicode spécifiques dans ODBC 3,0. Étant donné que ces spécifications ont changé dans ODBC 3,5, il est nécessaire d’avoir la version 1,5 ou ultérieure du fournisseur lors de l’utilisation de ODBC 3,5 et versions ultérieures. Cette section contient les rubriques suivantes :  
  
-   [Composants d’installation](../../../odbc/reference/install/installation-components.md)  
  
-   [Nombre d’utilisations](../../../odbc/reference/install/usage-counting.md)
