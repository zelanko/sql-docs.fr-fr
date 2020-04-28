---
title: Composants d’installation | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
- ODBC [ODBC], component installation
ms.assetid: 9de15ca0-fe6a-4634-8709-a928d3c9cc73
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0a196e9b935229fa03c6dd0eda92b8e99e69f0ca
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "81285249"
---
# <a name="installation-components"></a>Composants d’installation
> [!NOTE]  
>  À compter de Windows XP et de Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous devez uniquement installer explicitement ODBC sur les versions antérieures de Windows.  
  
 Le processus d’installation démarre lorsque l’utilisateur exécute le programme d’installation. Le programme d’installation de fonctionne conjointement avec la *dll* du programme d’installation et une *dll d’installation du pilote* pour chaque pilote. Le programme d’installation et la DLL du programme d’installation utilisent les arguments des fonctions **SQLInstallDriverEx** et **SQLInstallTranslatorEx** pour déterminer les fichiers à copier ou à supprimer pour chaque composant. L’illustration suivante montre la relation entre ces composants d’installation.  
  
 ![Relation entre composants d'installation](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]
>  Le fichier ODBC. inf utilisé dans ODBC *2. x* pour décrire les fichiers requis par chaque composant ODBC n’est pas utilisé dans ODBC *3. x*. Les pilotes qui livrent les composants ODBC *3. x* n’ont pas besoin de créer un fichier ODBC. inf. La suppression de **SQLInstallDriver** et **SQLInstallODBC**, ainsi que la désapprobation de **sqlinstalltranslator,**, ont rendu ODBC. inf inutile. Les informations de pilote qui se trouvaient dans les sections de mot clé Driver d’ODBC. inf sont désormais fournies dans l’argument *lpszDriver* dans **SQLInstallDriverEx**. Les informations de traducteur qui se trouvaient dans les sections [convertisseur ODBC] et spécification du traducteur d’ODBC. inf sont désormais fournies dans l’argument *lpszTranslator* de **SQLInstallTranslatorEx**. Ces modifications permettent au programme d’installation ODBC d’être plus portable sur plusieurs plateformes.  
  
 Pour plus d’informations sur ces composants, consultez les rubriques suivantes à la fin de cette section.  
  
-   [Programme d’installation](../../../odbc/reference/install/setup-program.md)  
  
-   [DLL d’installation](../../../odbc/reference/install/installer-dll.md)  
  
-   [DLL de configuration de pilote](../../../odbc/reference/install/driver-setup-dll.md)
