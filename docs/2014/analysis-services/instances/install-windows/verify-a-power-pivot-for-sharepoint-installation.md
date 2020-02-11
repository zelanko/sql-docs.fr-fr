---
title: Vérifier une installation de PowerPivot pour SharePoint | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
ms.assetid: 855bd055-5ad3-493f-9c5b-1f5297b2e6e2
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c4ce1b1485885719bcd31cb085d43379239612d3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66079865"
---
# <a name="verify-a-powerpivot-for-sharepoint-installation"></a>Vérifier une installation PowerPivot pour SharePoint
  Une instance de PowerPivot pour SharePoint que vous installez dans une batterie de serveurs SharePoint est administrée via l'Administration centrale de SharePoint. Au minimum, vous pouvez vérifier des pages dans l'Administration centrale et sur les sites SharePoint pour vérifier que les composants et fonctionnalités du serveur PowerPivot sont disponibles. Toutefois, pour une vérification complète, vous devez disposer d'un classeur PowerPivot que vous pouvez publier sur SharePoint et auquel vous pouvez accéder à partir d'une bibliothèque. Vous pouvez, à des fins de test, publier un classeur d'exemple contenant déjà des données PowerPivot et l'utiliser pour confirmer que l'intégration SharePoint est correctement configurée.  
  
##  <a name="verifyinstall"></a>Vérifier l’intégration de l’administration centrale  
 Pour vérifier l'intégration de PowerPivot avec l'Administration centrale, procédez comme suit :  
  
1.  Dans le menu Démarrer, cliquez sur **tous les programmes**, ouvrez produits Microsoft SharePoint 2010, puis cliquez sur **administration centrale de SharePoint 2010**.  
  
2.  Entrez votre nom d'utilisateur et votre mot de passe, puis cliquez sur **OK**.  
  
     Si vous le souhaitez, vous pouvez modifier des paramètres du navigateur pour ne pas avoir à entrer un nom d'utilisateur et un mot de passe chaque fois vous ouvrez l'Administration centrale. Pour ajouter l'Administration centrale comme site de confiance, procédez comme suit.  
  
    1.  Dans Internet Explorer, dans le menu Outils, cliquez sur **Options Internet**.  
  
    2.  Sous l'onglet Sécurité, dans la section **Cliquez sur une zone pour afficher ou modifier les paramètres de sécurité** , cliquez sur Sites de confiance, puis sur Sites.  
  
    3.  Décochez la case **Exiger un serveur sécurisé (https:) pour tous les sites de cette zone** .  
  
    4.  Dans **Ajouter ce site Web à la zone**, tapez l'URL à votre site, puis cliquez sur **Ajouter**.  
  
    5.  Cliquez sur **Fermer**, puis sur **OK**.  
  
        > [!NOTE]  
        >  La documentation d'installation de SharePoint inclut des instructions supplémentaires permettant de contourner des erreurs de serveur proxy et de désactiver l'option Configuration de sécurité renforcée d'Internet Explorer afin de pouvoir télécharger et installer des mises à jour. Pour plus d'informations, consultez la section **Effectuer des tâches supplémentaires** dans [Déployer un serveur unique avec SQL Server](https://go.microsoft.com/fwlink/?LinkId=177754) sur le site Web Microsoft.  
  
3.  Dans l'Administration centrale, sous Paramètres système, cliquez sur **Gérer les fonctionnalités des batteries de serveurs**.  
  
4.  Vérifiez que l'option **Fonctionnalité d'intégration PowerPivot** a la valeur **Activée**.  
  
5.  Dans l'Administration centrale, sous Paramètres système, cliquez sur **Gérer les services sur le serveur**.  
  
6.  Vérifiez que **SQL Server Analysis Services** et le **service système SQL Server PowerPivot** sont démarrés.  
  
7.  Dans administration centrale, dans gestion des applications, cliquez sur **gérer les applications de service**.  
  
8.  Cliquez sur **application de service PowerPivot par défaut** pour ouvrir le tableau de bord de gestion PowerPivot pour cette application. À la première utilisation, le tableau de bord prend plusieurs minutes à charger.  
  
     Vous pouvez également cliquer sur l’espace vide en regard de l' **application de service PowerPivot par défaut** pour sélectionner la ligne, puis cliquer sur **Propriétés** pour afficher les paramètres de configuration de cette application de service. Vous pouvez modifier à la fois des paramètres de configuration et des propriétés d'application pour modifier votre configuration du serveur. Pour plus d’informations sur ces paramètres, consultez [créer et configurer une application de service PowerPivot dans l’administration centrale](../../power-pivot-sharepoint/create-and-configure-power-pivot-service-application-in-ca.md).  
  
## <a name="verify-integration-at-the-site-level"></a>Vérifiez l'intégration au niveau du site  
 Pour vérifier l'intégration de PowerPivot avec un site SharePoint, procédez comme suit :  
  
1.  Dans un navigateur, ouvrez l'application Web que vous avez créée. Si vous avez utilisé des valeurs par défaut, vous\<pouvez spécifier http://le nom de votre ordinateur> dans l’adresse URL.  
  
2.  Vérifiez que l'accès aux données et les fonctionnalités de traitement de PowerPivot sont disponibles dans l'application. Pour cela, vous pouvez vérifier la présence de modèles de bibliothèque fournis par PowerPivot :  
  
    1.  Sur actions du site, cliquez sur **autres options.**..  
  
    2.  Dans les bibliothèques, vous devriez voir **bibliothèque de flux de données** et **Galerie PowerPivot**. Ces modèles de bibliothèque sont fournis par la fonctionnalité PowerPivot et sont visibles dans la liste des bibliothèques si la fonctionnalité est intégrée correctement.  
  
## <a name="verify-data-access-on-the-server"></a>Vérifiez l'accès aux données sur le serveur  
 Pour vérifier l'accès aux données PowerPivot sur le serveur, procédez comme suit :  
  
1.  [Téléchargez](https://go.microsoft.com/fwlink/?LinkID=219108) l’exemple de données Picnic qui accompagne un didacticiel Reporting Services. Vous allez utiliser l'exemple de classeur des fichiers téléchargés pour vérifier l'accès aux données PowerPivot. Procédez à l’extraction des fichiers.  
  
2.  Téléchargez le classeur Excel (.xlsx) dans Documents partagés. Le classeur contient des données PowerPivot incorporées.  
  
3.  Cliquez sur le document pour l'ouvrir à partir de la bibliothèque.  
  
4.  Cliquez sur un segment ou un filtre en haut du classeur. Mois, couleur et type sont des segments dans ce classeur. Cliquer sur un segment permet de lancer une requête PowerPivot et démontrer que votre serveur est opérationnel. Le serveur charge les données PowerPivot en arrière-plan et renvoie les résultats.  
  
5.  Revenez à la bibliothèque. Sélectionnez la flèche vers le bas située à droite du classeur, puis cliquez sur **Lancer Power View**. Cette étape confirme que la fonctionnalité [!INCLUDE[ssCrescent](../../../includes/sscrescent-md.md)] dans Reporting Services est opérationnelle. Si vous n'avez pas installé Reporting Services, ignorez cette étape.  
  
     À l'étape suivante, vous allez vous connecter au serveur dans Management Studio pour vérifier que les données sont chargées et mises en cache.  
  
6.  Démarrez SQL Server Management Studio à partir du groupe de programmes [!INCLUDE[ssSQL11](../../../includes/sssql11-md.md)] dans le menu Démarrer. Si cet outil n'est pas installé sur votre serveur, vous pouvez passer à la dernière étape pour confirmer la présence de fichiers mis en cache.  
  
7.  Dans Type de serveur, sélectionnez **Analysis Services**.  
  
8.  Dans nom du serveur, entrez ** \<Server-Name> \powerpivot**, où ** \<Server-Name>** correspond au nom de l’ordinateur sur lequel est installé le PowerPivot pour SharePoint.  
  
9. Cliquez sur **Connecter**. Le programme vérifie que le serveur Analysis Services est disponible.  
  
10. Dans l’Explorateur d’objets, vous pouvez cliquer sur **bases de données** pour afficher la liste des fichiers de données PowerPivot qui sont chargés.  
  
11. Sur le système de fichiers de l'ordinateur, vérifiez le dossier suivant pour déterminer si les fichiers sont mis en cache sur disque. La présence de fichiers mis en cache est une vérification supplémentaire que votre déploiement est opérationnel. Pour afficher le cache de fichiers, accédez au \<lecteur> : \Program Files\Microsoft SQL Server\MSAS11. Dossier d’application de service PowerPivot Powerpivot\olap\backup\sandboxes\dossier. Chaque base de données mise en cache est stockée dans son propre dossier, en utilisant une convention d'affectation de noms basés sur les GUID pour garantir un nom unique.  
  
  
