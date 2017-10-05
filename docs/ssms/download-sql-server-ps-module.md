---
title: "Télécharger le module PowerShell SQL Server | Microsoft Docs"
ms.custom: 
ms.date: 03/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
keywords:
- "installer powershell sql server, télécharger powershell sql server"
ms.assetid: 
caps.latest.revision: 113
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: d9a995f7d29fe91e14affa9266a9bce73acc9010
ms.openlocfilehash: 7449932a07aa0284fe2248828270b7f391713175
ms.contentlocale: fr-fr
ms.lasthandoff: 09/27/2017

---
# <a name="download-sql-server-powershell-module"></a>Télécharger le module PowerShell SQL Server
Le module PowerShell SQL Server fait partie de la version 17.0 de SQL Server Management Studio et il est désormais fourni via PowerShell Gallery.  Le module n’est plus inclus dans le package d’installation de SSMS. Pour utiliser PowerShell avec SSMS 17.0 et ultérieur, vous devez en plus installer le module SQL Server sur l’ordinateur.

Vous pouvez trouver une documentation complète sur l’installation de la dernière version de Windows Management Framework et sur l’installation en général des modules PowerShell sur le site [PowerShell Gallery](https://www.powershellgallery.com/).

La commande PowerShell pour installer le module SQL Server est :

> Install-Module -Name SqlServer

Cette commande installe le module pour tous les utilisateurs de l’ordinateur. Vous devez exécuter le processus PowerShell en tant qu’administrateur.

> Install-Module -Name SqlServer -Scope CurrentUser

Cette commande installe le module pour l’utilisateur qui exécute le processus PowerShell en cours. Vous n’avez pas besoin d’exécuter le processus PowerShell avec des droits d’administrateur.

S’il existe des versions antérieures des modules PowerShell SQL Server sur la machine, il peut être nécessaire d’ajouter le paramètre «-AllowClobber ».  

Si l’exécution se fait en tant qu’administrateur et pour installer le module pour tous les utilisateurs de l’ordinateur

> Install-Module -Name SqlServer -AllowClobber

Si l’exécution en tant qu’administrateur n’est pas possible ou pour installer seulement pour l’utilisateur actif

> Install-Module -Name SqlServer -Scope CurrentUser -AllowClobber

Quand des versions mises à jour du module SqlServer sont disponibles, vous pouvez mettre à jour la version en utilisant la commande Update-Module

> Update-Module -Name SqlServer

Pour afficher les versions du module installées sur la machine, vous pouvez utiliser

> Get-Module SqlServer -ListAvailable

Pour utiliser une version spécifique du module dans vos scripts, vous pouvez l’importer avec

> Import-Module SqlServer -Version 21.0.17178

Les versions du module PowerShell SQL Server incluses dans PowerShell Gallery prennent en charge la gestion de versions et nécessitent PowerShell version 5.0 ou ultérieure. Vous pouvez trouver le module SqlServer dans [PowerShell Gallery](https://www.powershellgallery.com/packages/Sqlserver/) 

