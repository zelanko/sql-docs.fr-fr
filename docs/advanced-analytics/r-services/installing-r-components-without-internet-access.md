---
title: "Installation des composants R sans acc&#232;s &#224; Internet | Microsoft Docs"
ms.custom: ""
ms.date: "02/10/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0a90c438-d78b-47be-ac05-479de64378b2
caps.latest.revision: 30
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 21
---
# Installation des composants R sans acc&#232;s &#224; Internet
  L’installation des composants R utilisés par [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] nécessite une connexion Internet pour l’accès aux fichiers disponibles sur le Centre de téléchargement Microsoft ou un autre site de confiance. Toutefois, vous pouvez installer ces composants sur un serveur sans accès à Internet, en créant des copies locales, comme indiqué dans cette rubrique.  
  
  > [!TIP]
  > 
  > Pour une description détaillée du processus d’installation hors connexion, consultez ce blog de [l’équipe de consultants clients de SQL Server](https://blogs.msdn.microsoft.com/sqlcat/2016/10/20/do-it-right-deploying-sql-server-r-services-on-computers-without-internet-access/)
  
## <a name="installation-on-computers-with-no-internet-access"></a>Installation sur des ordinateurs sans accès à Internet  
 Si vous effectuez une installation en mode hors connexion, [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] ne peut pas accéder aux liens permettant d’installer les composants R. Pour éviter ce problème, vous pouvez télécharger une copie des programmes d’installation en local et effectuer la configuration comme décrit ici.
 
 Notez qu’il existe deux programmes d’installation pour les composants R : un pour Microsoft R Open et l’autre pour Microsoft R Server. Vous devez télécharger et installer les deux pour utiliser SQL Server R Services. L’Assistant de configuration de SQL Server garantit qu’ils sont installés dans le bon ordre.


Version  |Télécharger le lien  
---------|---------
**SQL Server 2016 RTM**     |           
Microsoft R Open     |[SRO_3.2.2.803_1033.cab](https://go.microsoft.com/fwlink/?LinkId=761266)     
Microsoft R Server     |[SRS_8.0.3.0_1033.cab](https://go.microsoft.com/fwlink/?LinkId=735051)      
**SQL Server 2016 CU 1**     |           
Microsoft R Open     |[SRO_3.2.2.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808803)     
Microsoft R Server     |[SRS_8.0.3.10000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=808805)      
**SQL Server 2016 CU 2**     |           
Microsoft R Open     |[SRO_3.2.2.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827398)     
Microsoft R Server     |[SRS_8.0.3.12000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=827399)  
**SQL Server 2016 CU 3**     |           
Microsoft R Open     |[SRO_3.2.2.13000_1033.cab : ](https://go.microsoft.com/fwlink/?LinkId=831785)     
Microsoft R Server     |[SRS_8.0.3.13000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=831676)  |
**SQL Server 2016 SP 1**     |           
Microsoft R Open     |[SRO_3.2.2.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824879)     
Microsoft R Server     |[SRS_8.0.3.15000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=824881)  
**SQL Server 2016 SP 1 GDR**     |           
Microsoft R Open     |[SRO_3.2.2.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836819)     
Microsoft R Server     |[SRS_8.0.3.16000_1033.cab](https://go.microsoft.com/fwlink/?LinkId=836818)  

  
**Comment mettre à jour des composants R dans une installation hors connexion**     

1. Utilisez les liens ci-dessus pour télécharger la version appropriée.
2. Copiez les fichiers CAB vers un dossier sur l’ordinateur où vous voulez installer la mise à jour.
3. Lorsque vous exécutez l’Assistant de configuration de SQL Server, cliquez sur **Accepter** sur la page de gestion des licences Microsoft R.  Une boîte de dialogue répertoriant les liens vers les téléchargements s’affiche. Entrez le chemin d’accès à l’emplacement des fichiers téléchargés. 
4. Cliquez sur **Suivant** pour indiquer que les composants sont disponibles, et terminez l’Assistant de configuration de SQL Server.
5. Si vous le souhaitez, vous pouvez également télécharger le code source archivé pour les composants open source. Pour plus d’informations, consultez [Configurer SQL Server R Services](../../advanced-analytics/r-services/set-up-sql-server-r-services-in-database.md).


> [!IMPORTANT] Si vous téléchargez les fichiers .cab dans le cadre de la configuration de SQL Server sur un ordinateur connecté à Internet, l’Assistant de configuration détecte la langue locale et change automatiquement la langue du programme d’installation. 
> 
> Toutefois, si vous installez l’une des versions localisées de SQL Server sur un ordinateur sans accès à Internet et téléchargez les programmes d’installation de R vers un partage local, vous devez modifier manuellement le nom des fichiers téléchargés et insérer l’identificateur de langue approprié pour la langue que vous installez. 
> 
> Par exemple, si vous installez la version japonaise de SQL Server, vous remplacerez le nom du fichier SRS_8.0.3.0_1033.cab par SRS_8.0.3.0_1041.cab.    
 
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main de SQL Server R Services](../../advanced-analytics/r-services/getting-started-with-sql-server-r-services.md)   
 [Résoudre les problèmes d’installation liés à R Services](../Topic/Troubleshooting%20R%20Services%20Setup.md)  
  
  