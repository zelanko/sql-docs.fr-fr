---
title: "La connexion de données utilise l'authentification Windows, et les informations d'identification utilisateur n'ont pas pu être déléguées. Impossible d’actualiser les connexions suivantes : données PowerPivot | Documents Microsoft"
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2006df1-d244-4786-b272-49d8996cc88c
caps.latest.revision: 5
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7598685ddb6cd92ad3bcddd1bd307f976db88f55
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36154280"
---
# <a name="the-data-connection-uses-windows-authentication-and-user-credentials-could-not-be-delegated-the-following-connections-failed-to-refresh-powerpivot-data"></a>La connexion de données utilise l'authentification Windows, et les informations d'identification utilisateur n'ont pas pu être déléguées. Échec de l'actualisation des connexions suivantes : Données PowerPivot
  Pour les classeurs Excel contenant des données PowerPivot, Excel Services retourne cette erreur s'il ne peut pas se connecter à une instance de serveur PowerPivot dans SharePoint.  
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|S'applique à|PowerPivot pour SharePoint|  
|Version du produit|[!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)], [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)], [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]|  
|Cause|Échec de connexion lors d'une tentative d'utilisation d'un fournisseur de données PowerPivot.|  
|Texte du message|La connexion de données utilise l'authentification Windows, et les informations d'identification utilisateur n'ont pas pu être déléguées. Échec de l'actualisation des connexions suivantes : Données PowerPivot|  
  
## <a name="explanation"></a>Explication  
 Ce message d'erreur peut s'afficher pour plusieurs raisons. Le facteur qu'ils ont en commun est qu'Excel Services ne peut pas obtenir une identité de l'utilisateur Windows valide à partir d'un jeton de revendications dans SharePoint. Dans le cas des classeurs Excel contenant des données PowerPivot, cette erreur se produit lorsque l'une des conditions suivantes est respectée :  
  
-   Le service d'émission de jetons Revendications vers Windows n'est pas en cours d'exécution. Vous pouvez vérifier la cause de cette erreur en consultant le fichier journal SharePoint. Si les journaux SharePoint incluent le message « Le point de terminaison du canal 'net.pipe://localhost/s 4u/022694f3-9fbd-422b-b4b2-312e25dae2a2' est introuvable sur la machine locale », le service d'émission de jetons Revendications vers Windows n'est pas en cours d'exécution. Pour le démarrer, utilisez l'Administration centrale, puis vérifiez que le service est en cours d'exécution dans l'application console Services.  
  
-   Aucun contrôleur de domaine n'est disponible pour valider l'identité de l'utilisateur. Le service d'émission de jetons Revendications vers Windows n'utilise pas des informations d'identification mises en cache. Il valide l'identité de l'utilisateur pour chaque connexion. Vous pouvez vérifier la cause de cette erreur en consultant le fichier journal SharePoint. Si les journaux SharePoint incluent le message « Échec de l'obtention de WindowsIdentity à partir de IClaimsIdentity », l'identité de l'utilisateur n'a pas pu être authentifiée.  
  
-   Les ordinateurs doivent être membres du même domaine ou se trouver dans des domaines qui bénéficient dune relation d'approbation bidirectionnelle.  
  
-   Vous devez utiliser des comptes d'utilisateur de domaine Windows. Les comptes doivent avoir un nom d'utilisateur principal (UPN).  
  
-   Le compte de service Excel Services doit disposer d'autorisations Active Directory pour interroger l'objet.  
  
## <a name="user-action"></a>Action de l'utilisateur  
 Utilisez les instructions suivantes pour vérifier l'état du service d'émission de jetons Revendications vers Windows.  
  
 Pour tous les autres scénarios, contactez votre administrateur réseau.  
  
#### <a name="enable-claims-to-windows-token-service"></a>Activer le service d'émission de jetons Revendications vers Windows  
  
1.  Dans l'Administration centrale, sous Paramètres système, cliquez sur **Gérer les services sur le serveur**.  
  
2.  Sélectionnez **Service d'émission de jetons Revendications vers Windows**, puis cliquez sur **Démarrer**.  
  
3.  Vérifiez que le service est également en cours d'exécution dans la console Services :  
  
    1.  Dans Outils d'administration, cliquez sur Services.  
  
    2.  Démarrez le service d'émission de jetons Revendications vers Windows s'il n'est pas en cours d'exécution.  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les comptes de Service PowerPivot](configure-power-pivot-service-accounts.md)  
  
  