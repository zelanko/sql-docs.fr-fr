---
description: Installer des extensions dans SQL Server Management Studio (SSMS)
title: Installer des extensions dans SQL Server Management Studio (SSMS)
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
keywords:
- extensions
- vsix
- installer l'extension
- installer vsix
author: dzsquared
ms.author: drskwier
ms.reviewer: maghan
ms.custom: seo-lt-2019
ms.date: 07/29/2020
ms.openlocfilehash: bf4c9ee5287a2e0fdecf8455334561ce130499bc
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88492030"
---
# <a name="install-extensions-in-sql-server-management-studio-ssms"></a>Installer des extensions dans SQL Server Management Studio (SSMS)

[!INCLUDE [SQL Server ASDB, ASDBMI, ASDW ](../includes/applies-to-version/sql-asdb-asdbmi-asa.md)]

Les extensions SQL Server Management Studio (SSMS) sont créées avec C# via la charge de travail « développement d’extensions Visual Studio » dans Visual Studio. SSMS 18.x est basé sur le shell Visual Studio 2017 et est soumis aux limitations de cet environnement.

L’installation de l’extension dans SSMS 18.x peut s’effectuer en déployant le VSIX dans Visual Studio ou avec un programme d’installation de package géré indépendant.  Le déploiement Visual Studio est présenté ci-dessous.

> [!NOTE]
> Les extensions SQL Server Management Studio ne peuvent pas être installées via VSIXInstaller sous SSMS 18.x.
  
## <a name="visual-studio-deployment-of-an-extension-for-ssms-18x"></a>Déploiement Visual Studio d’une extension pour SSMS 18.x

L’installation manuelle de l’extension s’effectue en copiant les fichiers d’extension associés (VSIX) dans le dossier d’extensions SSMS par défaut.  SSMS recherche automatiquement les extensions dans ce dossier au lancement.  Le déploiement VSIX peut être effectué par Visual Studio au moment de la génération du projet. 

  
1.  Localisez votre installation de SSMS et le dossier d’extensions par défaut.  Avec les paramètres d’installation de SSMS par défaut, l’emplacement du dossier est ```C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\Extensions\```.  


2. Lancez Visual Studio en tant qu’administrateur.

3.  Le processus de copie de fichiers peut être effectué par Visual Studio au moment de la génération en activant la case à cocher « Copier le contenu VSIX à l’emplacement suivant» dans l’onglet VSIX de la fenêtre Propriétés du projet. Dans la zone de texte située sous la case à cocher, entrez l’emplacement du dossier ci-dessus en ajoutant un répertoire pour cette extension.  Par exemple : ```C:\Program Files (x86)\Microsoft SQL Server Management Studio 18\Common7\IDE\Extensions\SampleExtension```
  
![Paramètres VSIX dans la fenêtre Propriétés du projet avec 3 cases à cocher et une zone de texte](./media/install-extensions/vsix_ssms.png)

4. Générez le projet d’extension ; une build réussie transférera les fichiers d’extension vers le dossier d’extension SSMS.

5.  Lancez SSMS et testez les fonctionnalités de l’extension.
  
