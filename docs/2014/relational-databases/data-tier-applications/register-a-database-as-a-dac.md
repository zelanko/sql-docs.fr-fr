---
title: Inscrire une base de données en tant que DAC | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.registerdacwizard.registerdac.f1
- sql12.swb.registerdacwizard.summary.f1
- sql12.swb.registerdacwizard.introduction.f1
- sql12.swb.registerdacwizard.setproperties.f1
helpviewer_keywords:
- wizard [DAC], register
- How to [DAC], register
- register DAC
- data-tier application [SQL Server], register
ms.assetid: 08e52aa6-12f3-41dd-a793-14b99a083fd5
author: stevestein
ms.author: sstein
ms.openlocfilehash: e647ed8d563bb922ee083d7a10a57429148e954a
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84953086"
---
# <a name="register-a-database-as-a-dac"></a>Inscrire une base de données en tant que DAC
  Utilisez l' **Assistant inscrire l’application de la couche données** ou un script Windows PowerShell pour générer une définition d’application de la couche données (DAC) qui décrit les objets d’une base de données existante et enregistrez la définition de la DAC dans la `msdb` base de données système (**Master** dans [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] ).  
  
-   **Avant de commencer :**  [Limitations et restrictions](#LimitationsRestrictions), [Autorisations](#Permissions)  
  
-   **Pour mettre à niveau une DAC à l’aide de** :  [l’Assistant d’inscription de l’application de la couche Données](#UsingRegisterDACWizard), [PowerShell](#RegisterDACPowerShell)  
  
## <a name="before-you-begin"></a>Avant de commencer  
 Le processus d'inscription crée une définition de la DAC qui définit les objets de la base de données. La combinaison de la définition de la DAC et de la base de données forme une instance DAC. Si vous inscrivez une base de données comme une DAC sur une instance gérée du moteur de base de données, la DAC inscrite est incorporée dans l'utilitaire SQL Server la prochaine fois que le jeu d'éléments de collecte de l'utilitaire est envoyé de l'instance au point de contrôle de l'utilitaire. La DAC est ensuite présente dans le nœud **Application de la couche Données déployée** au sein de l’**Explorateur d’utilitaire** [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] et est signalée dans la page de détails pour **Application de la couche Données déployée**.  
  
###  <a name="limitations-and-restrictions"></a><a name="LimitationsRestrictions"></a> Limitations et restrictions  
 L'inscription de la DAC ne peut être exécutée que sur une base de données dans [!INCLUDE[ssSDS](../../includes/sssds-md.md)]ou [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] Service Pack 4 (SP4) ou version ultérieure. L'inscription de la DAC ne peut pas être effectuée si une DAC est déjà inscrite pour la base de données. Par exemple, si la base de données a été créée en déployant une DAC, vous ne pouvez pas exécuter l’ **Assistant Inscrire l’application de la couche Données**.  
  
 Vous ne pouvez pas inscrire de DAC si la base de données a des objets qui ne sont pas pris en charge dans une DAC, ou des utilisateurs à relation contenant-contenu. Pour plus d'informations sur les types d'objets pris en charge dans une DAC, consultez [DAC Support For SQL Server Objects and Versions](dac-support-for-sql-server-objects-and-versions.md).  
  
###  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 L’inscription d’une DAC dans une instance du [!INCLUDE[ssDE](../../includes/ssde-md.md)] nécessite au moins les autorisations ALTER ANY LOGIN et VIEW DEFINITION de l’étendue de la base de données, les autorisations SELECT sur **sys.sql_expression_dependencies**, et l’appartenance au rôle serveur fixe **dbcreator** . Les membres du rôle serveur fixe **sysadmin** ou le compte d’administrateur système intégré de SQL Server nommé **sa** peuvent également inscrire une DAC. L'inscription d'une DAC qui ne contient pas de connexions dans [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requiert l'appartenance aux rôles **dbmanager** ou **serveradmin** . L'inscription d'une DAC comportant des connexions dans [!INCLUDE[ssSDS](../../includes/sssds-md.md)] requiert l'appartenance aux rôles **loginmanager** ou **serveradmin** .  
  
##  <a name="using-the-register-data-tier-application-wizard"></a><a name="UsingRegisterDACWizard"></a> Utilisation de l'Assistant Inscrire l'application de la couche Données  
 **Pour inscrire une DAC à l'aide d'un Assistant**  
  
1.  Dans l' **Explorateur d'objets**, développez le nœud pour l'instance qui contient la base de données à inscrire en tant que DAC.  
  
2.  Développez le nœud **Bases de données** .  
  
3.  Cliquez avec le bouton droit sur la base de données à inscrire, pointez sur **Tâches**, puis sélectionnez **Inscrire en tant qu’application de la couche Données**.  
  
4.  Renseignez les boîtes de dialogue de l'Assistant :  
  
    1.  [Page Introduction](#Introduction)  
  
    2.  [Page Définir les propriétés](#Set_properties)  
  
    3.  [Page Validation et résumé](#Summary)  
  
    4.  [Page Inscrire la DAC](#Register)  
  
##  <a name="introduction-page"></a><a name="Introduction"></a> Page Introduction  
 Cette page décrit les étapes de l'inscription d'une application de la couche Données.  
  
 **Ne plus afficher cette page.** - Cochez la case pour ne plus afficher la page à l'avenir.  
  
 **Suivant >** : passe à la page **Définir les propriétés**.  
  
 **Annuler** : termine l’Assistant sans inscrire une DAC.  
  
##  <a name="set-properties-page"></a><a name="Set_properties"></a>Page définir les propriétés  
 Utilisez cette page pour spécifier des propriétés au niveau de la DAC telles que le nom de l'application et sa version.  
  
 **Nom de l’application.** - Chaîne qui spécifie le nom utilisé pour identifier la définition de la DAC. Le champ est renseigné avec le nom de la base de données.  
  
 **Version.** - Valeur numérique qui identifie la version de la DAC. La version de la DAC est utilisée dans Visual Studio pour identifier la version de la DAC sur laquelle les développeurs travaillent. Lors du déploiement d’une DAC, la version est stockée dans la `msdb` base de données et peut être affichée ultérieurement sous le nœud applications de la **couche données** dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] .  
  
 **Descriptive.** - Facultatif. Texte qui explique l'objectif de la DAC. Lors du déploiement d’une DAC, la description est stockée dans la `msdb` base de données et peut être affichée ultérieurement sous le nœud applications de la **couche données** dans [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)] .  
  
 ** \< Précédent** : vous renvoie à la page **Introduction** .  
  
 **Suivant >** : vérifie qu’une DAC peut être générée à partir des objets de la base de données et affiche les résultats dans la page **Validation et résumé**.  
  
 **Annuler** : termine l’Assistant sans inscrire la DAC.  
  
##  <a name="validation-and-summary-page"></a><a name="Summary"></a>Page validation et résumé  
 Utilisez cette page pour examiner les mesures que l'Assistant prendra lors de l'inscription de la DAC. La page passe par trois états alors qu'elle vérifie qu'une DAC peut être générée à partir des objets de la base de données.  
  
### <a name="retrieving-objects"></a>Récupération d'objets  
 **Récupération d'objets de bases de données et de serveurs.** - Affiche une barre de progression au fur et à mesure que l'Assistant récupère tous les objets requis de la base de données et de l'instance du moteur de base de données.  
  
 ** \< Précédent** : vous renvoie à la page **définir les propriétés** pour modifier vos entrées.  
  
 **Suivant >** : inscrit la DAC et affiche les résultats dans la page **Inscrire la DAC**.  
  
 **Annuler** : termine l’Assistant sans inscrire la DAC.  
  
### <a name="validating-objects"></a>Validation d'objets  
 **Vérification de**  _SchemaName_ **.** _ObjectName_ **.** - Affiche une barre de progression au fur et à mesure que l'Assistant vérifie les dépendances des objets récupérés, et vérifie que ces objets sont tous valides pour une DAC. _SchemaName_**.**_ObjectName_ identifient quel objet est vérifié actuellement.  
  
 ** \< Précédent** : vous renvoie à la page **définir les propriétés** pour modifier vos entrées.  
  
 **Suivant >** : inscrit la DAC et affiche les résultats dans la page **Inscrire la DAC**.  
  
 **Annuler** : termine l’Assistant sans inscrire la DAC.  
  
### <a name="summary"></a>Résumé  
 **Le paramètre suivant sera utilisé pour inscrire votre DAC.** - Affiche un rapport des propriétés et objets qui seront inclus dans la DAC.  
  
 **Enregistrer le rapport** : sélectionnez ce bouton pour enregistrer une copie du rapport de validation dans un fichier HTML. Le dossier par défaut est un dossier **SQL Server Management Studio\DAC Packages** dans le dossier Documents de votre compte Windows.  
  
 ** \< Précédent** : vous renvoie à la page **définir les propriétés** pour modifier vos entrées.  
  
 **Suivant >** : inscrit la DAC et affiche les résultats dans la page **Inscrire la DAC**.  
  
 **Annuler** : termine l’Assistant sans inscrire la DAC.  
  
##  <a name="register-dac-page"></a><a name="Register"></a>Page inscrire la DAC  
 Cette page signale la réussite ou l'échec de l'inscription.  
  
 **Inscription de la DAC** : signale la réussite ou l’échec de chaque action entreprise pour inscrire la DAC. Examinez les informations pour déterminer la réussite ou l'échec de chaque action. Toute action pour laquelle une erreur s'est produite aura un lien dans la colonne **Résultat** . Sélectionnez le lien pour consulter le rapport de d'erreur de cette action.  
  
 **Enregistrer le rapport** : sélectionnez ce bouton pour enregistrer le rapport d’inscription dans un fichier HTML. Le fichier signale l'état de chaque action, notamment toutes les erreurs générées par chacune des actions. Le dossier par défaut est un dossier **SQL Server Management Studio\DAC Packages** dans le dossier Documents de votre compte Windows. Le nom de fichier est au format \<DACPackageName>_RegisterDACReport_yyyymmdd.html, où \<*DACPackageName*> est le nom du package déployé, *aaaa* = l’année en cours, *mm* = le mois en cours et *JJ* = le jour actuel.  
  
 **Terminer** : met fin à l’Assistant.  
  
##  <a name="register-a-dac-using-powershell"></a><a name="RegisterDACPowerShell"></a>Inscrire une DAC à l’aide de PowerShell  
 **Pour inscrire une base de données comme DAC à l’aide de la méthode Register() dans un script PowerShell**  
  
1.  Créez un objet serveur SMO et définissez-le sur l'instance qui contient la base de données à inscrire comme une DAC.  
  
2.  Ajoutez une variable qui spécifie le nom de la base de données.  
  
3.  Spécifiez les métadonnées pour la DAC, par exemple le nom de la DAC, la version et la description.  
  
4.  Exécutez la méthode Register avec les informations spécifiées ci-dessus.  
  
### <a name="example-powershell"></a>Exemple (PowerShell)  
 L'exemple suivant inscrit une base de données nommée MyDB comme une DAC.  
  
```powershell
## Set a SMO Server object to the default instance on the local computer.  
CD SQLSERVER:\SQL\localhost\DEFAULT  
$srv = Get-Item .  
  
## Specify the database to register as a DAC.  
$dbname = "MyDB"  
  
## Specify the DAC metadata.  
$applicationname = "MyApplication"  
$version = "1.0.0.0"  
$description = "This DAC defines the database used by my application."  
  
## Register the DAC.  
$registerunit = New-Object Microsoft.SqlServer.Management.Dac.DacExtractionUnit($srv, $dbname, $applicationname, $version)  
$registerunit.Description = $description  
$registerunit.Register()  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Applications de la couche Données](data-tier-applications.md)  
