---
title: Prise en main de SSMA pour Sybase Console (SybaseToSQL) | Documents Microsoft
ms.custom: 
ms.date: 09/30/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: sql-ssma
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- Azure SQL Database
- SQL Server
helpviewer_keywords:
- Sybase Console,Launching SSMA Console
- Sybase Console,Output Conventions
- Sybase Console,Procedure for Using Console
ms.assetid: 43219dbe-bcfa-427d-9242-f07b1455f15f
caps.latest.revision: "22"
author: Shamikg
ms.author: Shamikg
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4929815714162459d17dfea3d7129a13b79558e3
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="getting-started-with-the-ssma-for-sybase-console-sybasetosql"></a>Prise en main de SSMA pour Sybase Console (SybaseToSQL)
Cette section décrit la procédure de lancement et de prise en main de SSMA pour Sybase console. Également répertoriés ici sont les conventions utilisées dans une fenêtre de sortie de Console de SSMA classique.  
  
## <a name="launching-the-ssma-console"></a>Lancer la Console SSMA  
Utilisez les étapes suivantes pour démarrer l’application de console SSMA :  
  
1.  Cliquez sur Démarrer, puis pointez sur tous les programmes.  
  
2.  Cliquez sur le **SQL Server Migration Assistant pour Sybase invite de commandes** contextuel.  
  
    Il affiche le menu de l’utilisation de SSMA Console et `(/? Help)`, pour vous aider à démarrer avec l’application console.  
  
## <a name="using-the-ssma-console"></a>À l’aide de la Console SSMA  
Une fois que la console est lancée correctement sur votre système Windows, vous pouvez utiliser les étapes suivantes pour travailler dessus :  
  
1.  Configurer la Console de SSMA via les fichiers de script. Pour plus d’informations sur cette section, consultez [création de fichiers de Script &#40; SybaseToSQL &#41; ](../../ssma/sybase/creating-script-files-sybasetosql.md).  
  
2.  [Création de fichiers de la valeur de la Variable &#40; SybaseToSQL &#41;](../../ssma/sybase/creating-variable-value-files-sybasetosql.md)  
  
3.  [Créer les fichiers de connexion de serveur &#40; SybaseToSQL &#41;](../../ssma/sybase/creating-the-server-connection-files-sybasetosql.md)  
  
4.  [L’exécution de la Console SSMA &#40; SybaseToSQL &#41; ](../../ssma/sybase/executing-the-ssma-console-sybasetosql.md) selon les besoins de votre projet. 
  
Fonctionnalités supplémentaires :  
  
1.  [Spécifiez un mot de passe](http://msdn.microsoft.com/en-us/9b6a70f9-6840-4140-a059-bb7bd7ccc67c) et d’importation/exportation vers d’autres ordinateurs de la fenêtre.  
  
2.  [Générer des rapports](http://msdn.microsoft.com/en-us/19278f6a-6d58-4867-9d71-c6228040466e) pour afficher le code xml détaillé la sortie des rapports pour la migration de données et d’évaluation ou de conversion. Vous pouvez également générer des rapports d’erreurs détaillées pour les commandes d’actualisation et la synchronisation.  
  
## <a name="ssma-console-output-conventions"></a>Conventions de sortie de Console de SSMA  
Lors de l’exécution des commandes de script SSMA et des options, le programme de console affiche les résultats et les messages (information, erreur, etc.) à l’utilisateur sur la console ou, si nécessaire, redirige vers un fichier de sortie xml. Chaque type de message dans la sortie est signalé par une couleur unique. Par exemple, le message de couleur blanche indique les commandes du fichier de script. celui de couleur verte représente une invite de commandes pour l’entrée d’utilisateur et ainsi de suite.  
  
![SSMAConsoleOutput_Sybase](../../ssma/sybase/media/ssmaconsoleoutput_sybase.JPG "SSMAConsoleOutput_Sybase")  
  
Couleur-interprétation de la sortie de console s’affiche dans le tableau suivant :  
  
|Color| Description|  
|---------|---------------|  
|Rouge|Erreur irrécupérable lors de l’exécution|  
|Gris|Cachet de date et heure, le message à l’utilisateur|  
|White|Commandes du fichier de script, le type de message|  
|Jaune|Avertissement|  
|Vert|Invite d’entrée d’utilisateur|  
|Cyan|Début, fin et le résultat d’une opération|  
  
## <a name="see-also"></a>Voir aussi  
[L’installation de SSMA pour SAP ASE &#40; SybaseToSQL &#41;](../../ssma/sybase/installing-ssma-for-sybase-sybasetosql.md)  
