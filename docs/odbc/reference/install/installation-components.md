---
title: Composants d’installation Microsoft Docs
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81285249"
---
# <a name="installation-components"></a>Composants d’installation
> [!NOTE]  
>  En commençant par Windows XP et Windows Server 2003, ODBC est inclus dans le système d’exploitation Windows. Vous ne devez installer explicitement ODBC que sur les versions antérieures de Windows.  
  
 Le processus d’installation commence lorsque l’utilisateur exécute le programme de configuration. Le programme d’installation fonctionne en conjonction avec *l’installateur DLL* et une *configuration du pilote DLL* pour chaque pilote. Le programme d’installation et l’installateur DLL utilisent les arguments des fonctions **SQLInstallDriverEx** et **SQLInstallTranslatorEx** pour déterminer quels fichiers copier ou supprimer pour chaque composant. L’illustration suivante montre la relation entre ces composants d’installation.  
  
 ![Relation entre composants d'installation](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]
>  Le fichier Odbc.inf qui a été utilisé dans ODBC *2.x* pour décrire les fichiers requis par chaque composant ODBC n’est pas utilisé dans ODBC *3.x*. Les conducteurs qui expédient des composants ODBC *3.x* n’ont pas besoin de créer un fichier Odbc.inf. L’enlèvement de **SQLInstallDriver** et **SQLInstallODBC**, et la dépréciation de **SQLInstallTranslator**, ont rendu Odbc.inf inutile. Les informations sur le conducteur qui se présentaient autrefois dans les sections Mot-clé du conducteur d’Odbc.inf sont maintenant fournies dans *l’argument de lpszDriver* dans **SQLInstallDriverEx**. Les informations de traducteur qui se présentaient autrefois dans les sections [ODBC Translator] et Translator Specification de Odbc.inf sont maintenant fournies dans *l’argument lpszTranslator* de **SQLInstallTranslatorEx**. Ces modifications permettent à l’installateur ODBC d’être plus portable sur toutes les plates-formes.  
  
 Pour plus d’informations sur ces composants, consultez les sujets suivants à la fin de cette section.  
  
-   [Programme d’installation](../../../odbc/reference/install/setup-program.md)  
  
-   [DLL d’installation](../../../odbc/reference/install/installer-dll.md)  
  
-   [DLL de configuration de pilote](../../../odbc/reference/install/driver-setup-dll.md)
