---
title: Présentation des différences entre l’exécution locale et l’exécution distante | Microsoft Docs
ms.custom: ''
ms.date: 03/09/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- docset-sql-devref
- integration-services
ms.topic: reference
helpviewer_keywords:
- Integration Services packages, running
- packages [Integration Services], running
- packages [Integration Services], troubleshooting
ms.assetid: 610ee7d9-4fea-4aba-9395-57add826923b
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: af56b93fc4b14e542a5a9f6423e9064c848417be
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48158689"
---
# <a name="understanding-the-differences-between-local-and-remote-execution"></a>Présentation des différences entre l'exécution locale et l'exécution distante
  Les développeurs et administrateurs de packages doivent savoir qu'il existe des restrictions quant à l'emplacement d'exécution d'un package [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)].  
  
-   **Un package s’exécute sur le même ordinateur que le programme qui le lance**. Même lorsqu'un programme charge un package stocké à distance sur un autre serveur, le package s'exécute sur l'ordinateur local.  
  
-   **Vous pouvez exécuter un package à l’extérieur de l’environnement de développement uniquement sur un ordinateur où est installé Integration Services**. Vous ne pouvez pas exécuter de packages en dehors de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] sur un ordinateur client sur lequel [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] n'est pas installé, et les termes de votre licence [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] peuvent ne pas vous permettre d'installer [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur d'autres ordinateurs. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] est un composant serveur et n’est pas redistribuable aux ordinateurs clients. Pour exécuter des packages à partir d'un ordinateur client, vous devez les lancer de manière à garantir leur exécution sur le serveur.  
  
 Pour plus d'informations sur le chargement et l'exécution d'un package enregistré, consultez :  
  
-   [Chargement et exécution d’un package local par programmation](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)  
  
-   [Chargement et exécution d’un package distant par programmation](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)  
  
 Pour plus d'informations sur l'exécution d'un package et le chargement de sa sortie dans un programme personnalisé, consultez :  
  
-   [Chargement de la sortie d’un package local](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
![Icône Integration Services (petite)](../media/dts-16.gif "icône Integration Services (petite)")**rester jusqu'à la Date avec Integration Services** <br /> Pour obtenir les derniers téléchargements, articles, exemples et vidéos de Microsoft, ainsi que des solutions sélectionnées par la communauté, visitez la page [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] sur MSDN :<br /><br /> [Visitez la page Integration Services sur MSDN](http://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> Pour recevoir une notification automatique de ces mises à jour, abonnez-vous aux flux RSS disponibles sur la page.  
  
## <a name="see-also"></a>Voir aussi  
 [Chargement et exécution d’un package local par programmation](../run-manage-packages-programmatically/loading-and-running-a-local-package-programmatically.md)   
 [Chargement et exécution d’un package distant par programmation](../run-manage-packages-programmatically/loading-and-running-a-remote-package-programmatically.md)   
 [Chargement de la sortie d’un package local](../run-manage-packages-programmatically/loading-the-output-of-a-local-package.md)  
  
  
