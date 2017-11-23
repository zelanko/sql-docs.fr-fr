---
title: "Composants d’installation | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- installing ODBC components [ODBC], setup program
- ODBC [ODBC], component installation
ms.assetid: 9de15ca0-fe6a-4634-8709-a928d3c9cc73
caps.latest.revision: "10"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: On Demand
ms.openlocfilehash: e00b3288b224f054939c75201a7ddd44f70c374c
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2017
---
# <a name="installation-components"></a>Composants d’installation
> [!NOTE]  
>  ODBC à partir de Windows XP et Windows Server 2003, est inclus dans le système d’exploitation Windows. Vous devez explicitement uniquement installer ODBC dans les versions antérieures de Windows.  
  
 Le processus d’installation démarre lorsque l’utilisateur exécute le programme d’installation. Le programme d’installation fonctionne en association avec le *installer DLL* et un *DLL d’installation du pilote* pour chaque pilote. Le programme d’installation et le programme d’installation DLL utilisent les arguments dans le **SQLInstallDriverEx** et **SQLInstallTranslatorEx** fonctions pour déterminer les fichiers à copier ou supprimer pour chaque composant. L’illustration suivante montre la relation entre ces composants d’installation.  
  
 ![Relation entre composants d’installation](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]  
>  Le fichier Odbc.inf qui a été utilisé dans ODBC 2. *x* pour décrire les fichiers requis par chaque ODBC le composant n’est pas utilisé dans ODBC 3*.x*. Les pilotes fournis ODBC 3*.x* composants n’avez pas besoin de créer un fichier Odbc.inf. La suppression de **SQLInstallDriver** et **SQLInstallODBC ne**et l’abandon du **SQLInstallTranslator**, les ont rendus Odbc.inf inutiles. Les informations de pilote utilisés dans les sections de mot clé Driver de Odbc.inf sont désormais fournies dans le *lpszDriver* argument dans **SQLInstallDriverEx**. Les informations de traduction qui permet de se trouver dans le [traducteur ODBC] et des sections de spécification de conversion de Odbc.inf est désormais fournie dans le *lpszTranslator* argument de **SQLInstallTranslatorEx**. Ces modifications permettent le programme d’installation de ODBC être plus portable sur plusieurs plateformes.  
  
 Pour plus d’informations sur ces composants, consultez les rubriques suivantes à la fin de cette section.  
  
-   [Programme d’installation](../../../odbc/reference/install/setup-program.md)  
  
-   [DLL d’installation](../../../odbc/reference/install/installer-dll.md)  
  
-   [DLL de configuration de pilote](../../../odbc/reference/install/driver-setup-dll.md)
