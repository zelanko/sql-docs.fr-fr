---
title: Configurations du package | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- package configuration syntax [Integration Services]
- SQL Server Integration Services packages, configurations
- SSIS packages, configurations
- XML [Integration Services]
- Integration Services packages, configurations
- configuration syntax [Integration Services]
- indirect configurations [Integration Services]
- configurations [Integration Services]
- direct configurations [Integration Services]
- packages [Integration Services], configurations
ms.assetid: d20e0311-1fc9-4ddc-a381-6d127cf11b69
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 84ad905a0b9e19c27e8b24bf9d4b2d0329a7db2c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85423916"
---
# <a name="package-configurations"></a>Configurations du package
  [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)][!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]fournit des configurations de package que vous pouvez utiliser pour mettre à jour les valeurs des propriétés au moment de l’exécution.  
  
> [!NOTE]  
>  Des configurations sont disponibles pour le modèle de déploiement de package. Les paramètres sont utilisés à la place des configurations pour le modèle de déploiement de projet. Le modèle de déploiement de projet vous permet de déployer des projets [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] sur le serveur [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] . Pour plus d'informations sur les modèles de déploiement, consultez [Deployment of Projects and Packages](packages/deploy-integration-services-ssis-projects-and-packages.md).  
  
 Une configuration est une paire propriété/valeur que vous ajoutez à un package terminé. En règle générale, vous devez créer un package, définir des propriétés sur les objets du package lors du développement de ce dernier, puis ajouter la configuration au package. Lors de son exécution, le package extrait les nouvelles valeurs de la propriété à partir de la configuration. Par exemple, lorsque vous utilisez une configuration, vous pouvez modifier la chaîne de connexion d'un gestionnaire de connexions ou mettre à jour la valeur d'une variable.  
  
 Les configurations de package offrent les avantages suivants :  
  
-   Les configurations facilitent le déplacement des packages d'un environnement de développement vers un environnement de production. Par exemple, une configuration peut mettre à jour le chemin d'accès d'un fichier source ou bien modifier le nom d'une base de données ou d'un serveur.  
  
-   Les configurations sont utiles lorsque vous déployez des packages sur de nombreux serveurs différents. Par exemple, une variable dans la configuration de chaque package déployé peut contenir une valeur d'espace disque différente, et si l'espace disque disponible ne correspond pas à cette valeur, le package ne s'exécute pas.  
  
-   Les configurations rendent ces packages plus souples. Par exemple, une configuration peut mettre à jour la valeur d'une variable utilisée dans une expression de propriété.  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] prend en charge différentes méthodes de stockage des configurations de package, telles que les fichiers XML, les tables d'une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et les variables d'environnement et de package.  
  
 Chaque configuration est une paire propriété/valeur. Le fichier de configuration XML et les types de configuration [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peuvent inclure plusieurs configurations.  
  
 Les configurations sont incluses lorsque vous créez un utilitaire de déploiement de package pour l'installation des packages. Lorsque vous installez les packages, les configurations peuvent être mises à jour lors d'une étape de l'installation du package.  
  
## <a name="understanding-how-package-configurations-are-applied-at-run-time"></a>Fonctionnement de l'application des configurations de package au moment de l'exécution  
 Quand vous utilisez l’utilitaire d’invite de commandes **dtexec** (dtexec.exe) pour exécuter un package déployé, l’utilitaire applique les configurations de package à deux reprises. L'utilitaire applique les configurations avant et après avoir appliqué les options que vous avez spécifiées sur la ligne de commande.  
  
 Lorsque l'utilitaire charge et exécute le package, des événements se produisent dans l'ordre suivant :  
  
1.  L’utilitaire **dtexec** charge le package.  
  
2.  L'utilitaire applique les configurations spécifiées dans le package au moment de la conception et dans l'ordre spécifié dans le package. (La seule exception concerne les configurations des variables de package parent. L'utilitaire applique ces configurations une seule fois et ultérieurement au cours du processus).  
  
3.  L'utilitaire applique ensuite les options que vous avez spécifiées sur la ligne de commande.  
  
4.  L'utilitaire recharge ensuite les configurations spécifiées dans le package au moment du design et dans l'ordre spécifié dans le package. (Une fois encore, la seule exception à cette règle concerne les configurations des variables de package parent). L'utilitaire se base sur les options de ligne de commande spécifiées pour recharger les configurations. Par conséquent, des valeurs différentes peuvent être rechargées à partir d'un emplacement distinct.  
  
5.  L'utilitaire applique les configurations des variables de package parent.  
  
6.  L'utilitaire exécute le package.  
  
 La façon dont l’utilitaire **dtexec** applique les configurations affecte les options de ligne de commande suivantes :  
  
-   Vous pouvez utiliser l’option **/Connection** ou **/Set** à l’exécution pour charger les configurations de package à partir d’un emplacement autre que celui que vous avez spécifié au moment de la conception.  
  
-   Vous pouvez utiliser l’option **/ConfigFile** pour charger des configurations supplémentaires que vous n’aviez pas spécifiées au moment de la conception.  
  
 Toutefois, ces options de ligne de commande sont soumises à quelques restrictions :  
  
-   Vous ne pouvez pas utiliser l’option **/Set** ou **/Connection** pour remplacer des valeurs uniques qui sont également définies par une configuration.  
  
-   Vous ne pouvez pas utiliser l’option **/ConfigFile** pour charger des configurations qui remplacent celles que vous aviez spécifiées au moment de la conception.  
  
 Pour plus d’informations sur ces options et sur la façon dont le comportement de ces options diffère entre [!INCLUDE[ssISCurrent](../includes/ssiscurrent-md.md)] et les versions antérieures, consultez [modification du comportement des fonctionnalités de Integration Services dans SQL Server 2014](../../2014/integration-services/behavior-changes-to-integration-services-features-in-sql-server-2014.md).  
  
## <a name="package-configuration-types"></a>Types de configuration de package  
 Le tableau suivant décrit les types de configuration de package.  
  
|Type|Description|  
|----------|-----------------|  
|Fichier de configuration XML|Un fichier XML contient les configurations. Le fichier XML peut inclure plusieurs configurations.|  
|Variable d’environnement|Une variable d'environnement contient la configuration.|  
|Entrée de Registre|Une entrée de Registre contient la configuration.|  
|Variable de package parent|Une variable dans le package contient la configuration. Ce type de configuration est généralement utilisé pour mettre à jour les propriétés dans les packages enfants.|  
|Table [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Une table d'une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] contient la configuration. La table peut inclure plusieurs configurations.|  
  
### <a name="xml-configuration-files"></a>Fichiers de configuration XML  
 Si vous sélectionnez le type de configuration **Fichier de configuration XML** , vous pouvez créer un nouveau fichier de configuration, réutiliser un fichier existant et ajouter de nouvelles configurations, ou réutiliser un fichier existant en remplaçant son contenu.  
  
 Un fichier de configuration XML est composé de deux sections :  
  
-   Un en-tête qui contient des informations sur le fichier de configuration. Cet élément comprend des attributs tels que la date de création du fichier et le nom de la personne qui a généré le fichier.  
  
-   Les éléments de configuration qui contiennent des informations sur chaque configuration. Cet élément comprend des attributs tels que le chemin d'accès de la propriété et la valeur configurée de la propriété.  
  
 Le code XML suivant présente la syntaxe d'un fichier de configuration XML. Cet exemple montre une configuration de la propriété Valeur d’une variable de type entier nommée `MyVar`.  
  
```  
<?xml version="1.0"?>  
<DTSConfiguration>  
   <DTSConfigurationHeading>  
      <DTSConfigurationFileInfo  
          GeneratedBy="DomainName\UserName"  
          GeneratedFromPackageName="Package"  
          GeneratedFromPackageID="{2AF06766-817A-4E28-9878-0DE37A150648}"  
          GeneratedDate="2/01/2005 5:58:09 PM"/>  
   </DTSConfigurationHeading>  
   <Configuration ConfiguredType="Property" Path="\Package.Variables[User::MyVar].Value" ValueType="Int32">  
      <ConfiguredValue>0</ConfiguredValue>  
   </Configuration>  
</DTSConfiguration>  
  
```  
  
### <a name="registry-entry"></a>Entrée de Registre  
 Si vous souhaitez utiliser une entrée de Registre pour stocker la configuration, vous pouvez utiliser une clé existante ou créer une nouvelle clé dans HKEY_CURRENT_USER. La clé de Registre que vous utilisez doit contenir une valeur nommée `Value`. Cette valeur peut être de type DWORD ou une chaîne.  
  
 Si vous sélectionnez le type de configuration **Entrée de Registre** , tapez le nom de la clé de Registre dans la zone d'entrée de Registre. Le format est \<registry key>. Si vous souhaitez utiliser une clé de Registre qui ne se trouve pas à la racine de HKEY_CURRENT_USER, utilisez le format \<Registry key\registry key\\...> pour identifier la clé. Par exemple, pour utiliser la clé MyPackage située dans SSISPackages, tapez `SSISPackages\MyPackage`.  
  
### <a name="sql-server"></a>SQL Server  
 Si vous sélectionnez le type de configuration **SQL Server** , vous spécifiez la connexion à la base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] dans laquelle vous voulez stocker les configurations. Vous pouvez enregistrer les configurations dans une table existante ou créer une nouvelle table dans la base de données spécifiée.  
  
 L'instruction SQL suivante montre l'instruction CREATE TABLE par défaut fournie par l'Assistant Configuration de package.  
  
```  
CREATE TABLE [dbo].[SSIS Configurations]  
(  
ConfigurationFilter NVARCHAR(255) NOT NULL,  
ConfiguredValue NVARCHAR(255) NULL,  
PackagePath NVARCHAR(255) NOT NULL,  
ConfiguredValueType NVARCHAR(20) NOT NULL  
)  
  
```  
  
 Le nom que vous donnez à la configuration est la valeur stockée dans la colonne **ConfigurationFilter** .  
  
## <a name="direct-and-indirect-configurations"></a>Configurations directes et indirectes  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] fournit des configurations directes et indirectes. Si vous spécifiez directement les configurations, [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] crée un lien direct entre l'élément de configuration et la propriété de l'objet package. Les configurations directes sont un meilleur choix lorsque l'emplacement de la source ne change pas. Par exemple, si vous êtes sûr que tous les déploiements dans le package utilisent le même chemin d'accès de fichier, vous pouvez spécifier un fichier de configuration XML.  
  
 Les configurations indirectes utilisent des variables d'environnement. Au lieu de spécifier directement le paramètre de configuration, la configuration pointe vers une variable d'environnement, qui contient à son tour la valeur de configuration. L'utilisation de configurations indirectes est un meilleur choix lorsque l'emplacement de la configuration peut changer pour chaque déploiement d'un package.  
  
## <a name="related-tasks"></a>Tâches associées  
 [Créer des configurations de package](../../2014/integration-services/create-package-configurations.md)  
  
## <a name="related-content"></a>Contenu associé  
  
-   Article technique, [Understanding Integration Services Package Configurations](https://go.microsoft.com/fwlink/?LinkId=165643), sur msdn.microsoft.com  
  
-   Entrée de blog, [création de packages dans le code-configurations de package](https://go.microsoft.com/fwlink/?LinkId=217663), sur www.SQLIS.com.  
  
-   Entrée de blog, [exemple d’API-ajouter par programmation un fichier de configuration à un package](https://go.microsoft.com/fwlink/?LinkId=217664), sur blogs.msdn.com.  
  
  
