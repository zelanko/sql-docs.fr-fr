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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 34d1b6d143f6f40d73e2feeb0b718f3c3b3248fe
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2019
ms.locfileid: "68094135"
---
# <a name="installation-components"></a>Composants d’installation
> [!NOTE]  
>  ODBC à partir de Windows XP et Windows Server 2003, est inclus dans le système d’exploitation Windows. Vous devez explicitement uniquement installer ODBC dans les versions antérieures de Windows.  
  
 Le processus d’installation démarre lorsque l’utilisateur exécute le programme d’installation. Le programme d’installation fonctionne conjointement avec le *DLL d’installation* et un *DLL d’installation du pilote* pour chaque pilote. Le programme d’installation et le programme d’installation DLL utilisent les arguments dans le **SQLInstallDriverEx** et **SQLInstallTranslatorEx** fonctions pour déterminer les fichiers à copier ou supprimer pour chaque composant. L’illustration suivante montre la relation entre ces composants d’installation.  
  
 ![Relation entre composants d’installation](../../../odbc/reference/install/media/pr29.gif "pr29")  
  
> [!IMPORTANT]
>  Le fichier Odbc.inf qui a été utilisé dans ODBC *2.x* pour décrire les fichiers requis par chaque ODBC le composant n’est pas utilisé dans ODBC *3.x*. Les pilotes fournis ODBC *3.x* composants n’êtes pas obligé de créer un fichier Odbc.inf. La suppression de **SQLInstallDriver** et **SQLInstallODBC ne**et le fait de déconseiller **SQLInstallTranslator**, les ont rendus Odbc.inf inutiles. Les informations de pilote qui existaient dans les sections de mot clé Driver de Odbc.inf sont désormais fournies dans le *lpszDriver* argument dans **SQLInstallDriverEx**. Les informations de traducteur qui existaient dans le [traducteur ODBC] et les sections de spécification de traducteur de Odbc.inf est désormais fourni dans le *lpszTranslator* argument de **SQLInstallTranslatorEx**. Ces modifications permettent le programme d’installation de ODBC être plus portable sur plusieurs plateformes.  
  
 Pour plus d’informations sur ces composants, consultez les rubriques suivantes à la fin de cette section.  
  
-   [Programme d’installation](../../../odbc/reference/install/setup-program.md)  
  
-   [DLL d’installation](../../../odbc/reference/install/installer-dll.md)  
  
-   [DLL de configuration de pilote](../../../odbc/reference/install/driver-setup-dll.md)
