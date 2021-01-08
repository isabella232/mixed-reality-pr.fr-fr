---
title: Informations de référence sur les API du portail d’appareil
description: Restez à jour sur l’API du portail d’appareils Windows pour le développement HoloLens.
author: hamalawi
ms.author: moelhama
ms.date: 08/03/2020
ms.topic: article
keywords: HoloLens, portail des appareils Windows, API, casque de réalité mixte, casque Windows Mixed realisation, casque de réalité virtuelle
ms.openlocfilehash: 13845a5a5668ee8c86178196326425f46be9b321
ms.sourcegitcommit: 2329db5a76dfe1b844e21291dbc8ee3888ed1b81
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2021
ms.locfileid: "98006649"
---
# <a name="device-portal-api-reference"></a><span data-ttu-id="ee3fe-104">Informations de référence sur les API du portail d’appareil</span><span class="sxs-lookup"><span data-stu-id="ee3fe-104">Device portal API reference</span></span>

<span data-ttu-id="ee3fe-105">Tout ce qui se trouve dans le [portail de périphériques Windows](using-the-windows-device-portal.md) repose sur des API REST que vous pouvez utiliser pour accéder aux données et contrôler votre appareil par programme.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-105">Everything in the [Windows Device Portal](using-the-windows-device-portal.md) is built on top of REST API's that you can use to access the data and control your device programmatically.</span></span>

## <a name="app-deloyment"></a><span data-ttu-id="ee3fe-106">Déploiement de l’application</span><span class="sxs-lookup"><span data-stu-id="ee3fe-106">App deloyment</span></span>

<span data-ttu-id="ee3fe-107">**/API/App/packagemanager/package (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-107">**/api/app/packagemanager/package (DELETE)**</span></span>

<span data-ttu-id="ee3fe-108">Désinstalle une application</span><span class="sxs-lookup"><span data-stu-id="ee3fe-108">Uninstalls an app</span></span>

<span data-ttu-id="ee3fe-109">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-109">Parameters</span></span>
* <span data-ttu-id="ee3fe-110">Package : nom de fichier du package à désinstaller.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-110">package : File name of the package to be uninstalled.</span></span>

<span data-ttu-id="ee3fe-111">**/API/App/packagemanager/package (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-111">**/api/app/packagemanager/package (POST)**</span></span>

<span data-ttu-id="ee3fe-112">Installe une application</span><span class="sxs-lookup"><span data-stu-id="ee3fe-112">Installs an App</span></span>

<span data-ttu-id="ee3fe-113">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-113">Parameters</span></span>
* <span data-ttu-id="ee3fe-114">Package : nom de fichier du package à installer.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-114">package : File name of the package to be installed.</span></span>

<span data-ttu-id="ee3fe-115">Payload</span><span class="sxs-lookup"><span data-stu-id="ee3fe-115">Payload</span></span>
* <span data-ttu-id="ee3fe-116">corps http en plusieurs parties, conforme</span><span class="sxs-lookup"><span data-stu-id="ee3fe-116">multi-part conforming http body</span></span>

<span data-ttu-id="ee3fe-117">**/API/App/packagemanager/packages (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-117">**/api/app/packagemanager/packages (GET)**</span></span>

<span data-ttu-id="ee3fe-118">Récupère la liste des applications installées sur le système, avec les détails</span><span class="sxs-lookup"><span data-stu-id="ee3fe-118">Retrieves the list of installed apps on the system, with details</span></span>

<span data-ttu-id="ee3fe-119">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="ee3fe-119">Return data</span></span>
* <span data-ttu-id="ee3fe-120">Liste des packages installés avec des détails</span><span class="sxs-lookup"><span data-stu-id="ee3fe-120">List of installed packages with details</span></span>

<span data-ttu-id="ee3fe-121">**/API/App/packagemanager/State (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-121">**/api/app/packagemanager/state (GET)**</span></span>

<span data-ttu-id="ee3fe-122">Obtient l’état de l’installation de l’application en cours</span><span class="sxs-lookup"><span data-stu-id="ee3fe-122">Gets the status of in progress app installation</span></span>

## <a name="dump-collection"></a><span data-ttu-id="ee3fe-123">Collection de vidages</span><span class="sxs-lookup"><span data-stu-id="ee3fe-123">Dump collection</span></span>

<span data-ttu-id="ee3fe-124">**/API/Debug/dump/usermode/CrashControl (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-124">**/api/debug/dump/usermode/crashcontrol (DELETE)**</span></span>

<span data-ttu-id="ee3fe-125">Désactive la collecte de vidages sur incident pour une application faisant</span><span class="sxs-lookup"><span data-stu-id="ee3fe-125">Disables crash dump collection for a sideloaded app</span></span>

<span data-ttu-id="ee3fe-126">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-126">Parameters</span></span>
* <span data-ttu-id="ee3fe-127">packageFullname : nom du package</span><span class="sxs-lookup"><span data-stu-id="ee3fe-127">packageFullname : package name</span></span>

<span data-ttu-id="ee3fe-128">**/API/Debug/dump/usermode/CrashControl (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-128">**/api/debug/dump/usermode/crashcontrol (GET)**</span></span>

<span data-ttu-id="ee3fe-129">Obtient les paramètres de la collection de vidages sur incident des applications faisant</span><span class="sxs-lookup"><span data-stu-id="ee3fe-129">Gets settings for sideloaded apps crash dump collection</span></span>

<span data-ttu-id="ee3fe-130">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-130">Parameters</span></span>
* <span data-ttu-id="ee3fe-131">packageFullname : nom du package</span><span class="sxs-lookup"><span data-stu-id="ee3fe-131">packageFullname : package name</span></span>

<span data-ttu-id="ee3fe-132">**/API/Debug/dump/usermode/CrashControl (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-132">**/api/debug/dump/usermode/crashcontrol (POST)**</span></span>

<span data-ttu-id="ee3fe-133">Active et définit les paramètres de contrôle de vidage pour une application faisant</span><span class="sxs-lookup"><span data-stu-id="ee3fe-133">Enables and sets dump control settings for a sideloaded app</span></span>

<span data-ttu-id="ee3fe-134">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-134">Parameters</span></span>
* <span data-ttu-id="ee3fe-135">packageFullname : nom du package</span><span class="sxs-lookup"><span data-stu-id="ee3fe-135">packageFullname : package name</span></span>

<span data-ttu-id="ee3fe-136">**/API/Debug/dump/usermode/crashdump (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-136">**/api/debug/dump/usermode/crashdump (DELETE)**</span></span>

<span data-ttu-id="ee3fe-137">Supprime un vidage sur incident pour une application faisant</span><span class="sxs-lookup"><span data-stu-id="ee3fe-137">Deletes a crash dump for a sideloaded app</span></span>

<span data-ttu-id="ee3fe-138">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-138">Parameters</span></span>
* <span data-ttu-id="ee3fe-139">packageFullname : nom du package</span><span class="sxs-lookup"><span data-stu-id="ee3fe-139">packageFullname : package name</span></span>
* <span data-ttu-id="ee3fe-140">fileName : nom du fichier dump</span><span class="sxs-lookup"><span data-stu-id="ee3fe-140">fileName : dump file name</span></span>

<span data-ttu-id="ee3fe-141">**/API/Debug/dump/usermode/crashdump (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-141">**/api/debug/dump/usermode/crashdump (GET)**</span></span>

<span data-ttu-id="ee3fe-142">Récupère un vidage sur incident pour une application faisant</span><span class="sxs-lookup"><span data-stu-id="ee3fe-142">Retrieves a crash dump for a sideloaded app</span></span>

<span data-ttu-id="ee3fe-143">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-143">Parameters</span></span>
* <span data-ttu-id="ee3fe-144">packageFullname : nom du package</span><span class="sxs-lookup"><span data-stu-id="ee3fe-144">packageFullname : package name</span></span>
* <span data-ttu-id="ee3fe-145">fileName : nom du fichier dump</span><span class="sxs-lookup"><span data-stu-id="ee3fe-145">fileName : dump file name</span></span>

<span data-ttu-id="ee3fe-146">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="ee3fe-146">Return data</span></span>
* <span data-ttu-id="ee3fe-147">Fichier dump.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-147">Dump file.</span></span> <span data-ttu-id="ee3fe-148">Inspecter avec WinDbg ou Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ee3fe-148">Inspect with WinDbg or Visual Studio</span></span>

<span data-ttu-id="ee3fe-149">**/API/Debug/dump/usermode/dumps (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-149">**/api/debug/dump/usermode/dumps (GET)**</span></span>

<span data-ttu-id="ee3fe-150">Retourne la liste de tous les vidages sur incident pour les applications faisant</span><span class="sxs-lookup"><span data-stu-id="ee3fe-150">Returns list of all crash dumps for sideloaded apps</span></span>

<span data-ttu-id="ee3fe-151">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="ee3fe-151">Return data</span></span>
* <span data-ttu-id="ee3fe-152">Liste des vidages sur incident par application à chargement latéral</span><span class="sxs-lookup"><span data-stu-id="ee3fe-152">List of crash dumps per side loaded app</span></span>

## <a name="etw"></a><span data-ttu-id="ee3fe-153">ETW</span><span class="sxs-lookup"><span data-stu-id="ee3fe-153">ETW</span></span>

<span data-ttu-id="ee3fe-154">**/API/ETW/Providers (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-154">**/api/etw/providers (GET)**</span></span>

<span data-ttu-id="ee3fe-155">Énumère les fournisseurs inscrits</span><span class="sxs-lookup"><span data-stu-id="ee3fe-155">Enumerates registered providers</span></span>

<span data-ttu-id="ee3fe-156">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="ee3fe-156">Return data</span></span>
* <span data-ttu-id="ee3fe-157">Liste des fournisseurs, nom convivial et GUID</span><span class="sxs-lookup"><span data-stu-id="ee3fe-157">List of providers, friendly name and GUID</span></span>

<span data-ttu-id="ee3fe-158">**/API/ETW/session/Realtime (obtient/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-158">**/api/etw/session/realtime (GET/WebSocket)**</span></span>

<span data-ttu-id="ee3fe-159">Crée une session ETW en temps réel ; géré sur un WebSocket.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-159">Creates a realtime ETW session; managed over a websocket.</span></span>

<span data-ttu-id="ee3fe-160">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="ee3fe-160">Return data</span></span>
* <span data-ttu-id="ee3fe-161">Événements ETW des fournisseurs activés</span><span class="sxs-lookup"><span data-stu-id="ee3fe-161">ETW events from the enabled providers</span></span>

## <a name="holographic-os"></a><span data-ttu-id="ee3fe-162">Système d’exploitation holographique</span><span class="sxs-lookup"><span data-stu-id="ee3fe-162">Holographic OS</span></span>

<span data-ttu-id="ee3fe-163">**/API/Holographic/OS/ETW/customproviders (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-163">**/api/holographic/os/etw/customproviders (GET)**</span></span>

<span data-ttu-id="ee3fe-164">Retourne une liste de fournisseurs ETW spécifiques à HoloLens qui ne sont pas inscrits auprès du système.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-164">Returns a list of HoloLens specific ETW providers that are not registered with the system</span></span>

<span data-ttu-id="ee3fe-165">**/API/Holographic/OS/services (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-165">**/api/holographic/os/services (GET)**</span></span>

<span data-ttu-id="ee3fe-166">Retourne les États de tous les services en cours d’exécution.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-166">Returns the states of all services running.</span></span>

<span data-ttu-id="ee3fe-167">**/API/Holographic/OS/Settings/IPD (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-167">**/api/holographic/os/settings/ipd (GET)**</span></span>

<span data-ttu-id="ee3fe-168">Obtient la IPD stockée (distance interpupillary) en millimètres.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-168">Gets the stored IPD (Interpupillary distance) in millimeters</span></span>

<span data-ttu-id="ee3fe-169">**/API/Holographic/OS/Settings/IPD (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-169">**/api/holographic/os/settings/ipd (POST)**</span></span>

<span data-ttu-id="ee3fe-170">Définit l’IPD</span><span class="sxs-lookup"><span data-stu-id="ee3fe-170">Sets the IPD</span></span>

<span data-ttu-id="ee3fe-171">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-171">Parameters</span></span>
* <span data-ttu-id="ee3fe-172">IPD : nouvelle valeur IPD à définir en millimètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-172">ipd : New IPD value to be set in millimeters</span></span>

<span data-ttu-id="ee3fe-173">**/API/Holographic/OS/webmanagement/Settings/HTTPS (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-173">**/api/holographic/os/webmanagement/settings/https (GET)**</span></span>

<span data-ttu-id="ee3fe-174">Obtenir la spécification HTTPS pour Device Portal</span><span class="sxs-lookup"><span data-stu-id="ee3fe-174">Get HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="ee3fe-175">**/API/Holographic/OS/webmanagement/Settings/HTTPS (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-175">**/api/holographic/os/webmanagement/settings/https (POST)**</span></span>

<span data-ttu-id="ee3fe-176">Définit les exigences HTTPs pour le portail de l’appareil</span><span class="sxs-lookup"><span data-stu-id="ee3fe-176">Sets HTTPS requirements for the Device Portal</span></span>

<span data-ttu-id="ee3fe-177">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-177">Parameters</span></span>
* <span data-ttu-id="ee3fe-178">obligatoire : Oui, non ou par défaut</span><span class="sxs-lookup"><span data-stu-id="ee3fe-178">required : yes, no or default</span></span>

## <a name="holographic-perception"></a><span data-ttu-id="ee3fe-179">Perception holographique</span><span class="sxs-lookup"><span data-stu-id="ee3fe-179">Holographic Perception</span></span>

<span data-ttu-id="ee3fe-180">**/API/Holographic/perception/client (obtient/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-180">**/api/holographic/perception/client (GET/WebSocket)**</span></span>

<span data-ttu-id="ee3fe-181">Accepte les mises à niveau de WebSocket et exécute un client de perception qui envoie des mises à jour à 30 i/s.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-181">Accepts websocket upgrades and runs a perception client that sends updates at 30 fps.</span></span>

<span data-ttu-id="ee3fe-182">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-182">Parameters</span></span>
* <span data-ttu-id="ee3fe-183">Clientmode : "active" force le mode de suivi visuel lorsqu’il ne peut pas être établi passivement</span><span class="sxs-lookup"><span data-stu-id="ee3fe-183">clientmode: "active" forces visual tracking mode when it can't be established passively</span></span>

## <a name="holographic-thermal"></a><span data-ttu-id="ee3fe-184">Thermique holographique</span><span class="sxs-lookup"><span data-stu-id="ee3fe-184">Holographic Thermal</span></span>

<span data-ttu-id="ee3fe-185">**/API/Holographic/thermal/stage (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-185">**/api/holographic/thermal/stage (GET)**</span></span>

<span data-ttu-id="ee3fe-186">Récupération de l’étape thermique de l’appareil (0 normal, 1 chaud, 2 critique)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-186">Get the thermal stage of the device (0 normal, 1 warm, 2 critical)</span></span>

## <a name="map-manager"></a><span data-ttu-id="ee3fe-187">Map Manager</span><span class="sxs-lookup"><span data-stu-id="ee3fe-187">Map Manager</span></span>

<span data-ttu-id="ee3fe-188">**/api/holographic/mapmanager/mapFiles (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-188">**/api/holographic/mapmanager/mapFiles (GET)**</span></span>

<span data-ttu-id="ee3fe-189">Obtient la liste des fichiers de mappage disponibles (. MapX).</span><span class="sxs-lookup"><span data-stu-id="ee3fe-189">Gets the list of the available map files (.mapx).</span></span>

<span data-ttu-id="ee3fe-190">**/api/holographic/mapmanager/anchorFiles (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-190">**/api/holographic/mapmanager/anchorFiles (GET)**</span></span>

<span data-ttu-id="ee3fe-191">Obtient la liste des fichiers d’ancrage disponibles (. ancx).</span><span class="sxs-lookup"><span data-stu-id="ee3fe-191">Gets the list of available anchor files (.ancx).</span></span>

<span data-ttu-id="ee3fe-192">**/api/holographic/mapmanager/srdbFiles (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-192">**/api/holographic/mapmanager/srdbFiles (GET)**</span></span>

<span data-ttu-id="ee3fe-193">Obtient la liste des fichiers de base de données de reconstruction spatiale disponibles (. srdb).</span><span class="sxs-lookup"><span data-stu-id="ee3fe-193">Gets the list of available spatial reconstruction database files (.srdb).</span></span>

<span data-ttu-id="ee3fe-194">**/API/Holographic/mapmanager/getanchors (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-194">**/api/holographic/mapmanager/getanchors (GET)**</span></span>

<span data-ttu-id="ee3fe-195">Obtient la liste des ancres persistantes pour l’utilisateur actuel.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-195">Gets the list of persisted anchors for the current user.</span></span> 

### <a name="downloaduploaddelete-files"></a><span data-ttu-id="ee3fe-196">Télécharger/Télécharger/supprimer des fichiers</span><span class="sxs-lookup"><span data-stu-id="ee3fe-196">Download/Upload/Delete Files</span></span>
<span data-ttu-id="ee3fe-197">**/API/Holographic/mapmanager/Download (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-197">**/api/holographic/mapmanager/download (GET)**</span></span>

<span data-ttu-id="ee3fe-198">Télécharge un fichier de base de données de carte, d’ancrage ou de reconstruction spatiale.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-198">Downloads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="ee3fe-199">Le fichier doit avoir été préalablement téléchargé ou exporté.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-199">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="ee3fe-200">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-200">Parameters</span></span>
* <span data-ttu-id="ee3fe-201">FileName : nom du fichier à télécharger.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-201">FileName: Name of file to download.</span></span>

<span data-ttu-id="ee3fe-202">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ee3fe-202">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/download?FileName=" + spaceID)
```

<span data-ttu-id="ee3fe-203">**/API/Holographic/mapmanager/upload (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-203">**/api/holographic/mapmanager/upload (POST)**</span></span>

<span data-ttu-id="ee3fe-204">Charge un fichier de base de données de carte, d’ancrage ou de reconstruction spatiale.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-204">Uploads a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="ee3fe-205">Une fois qu’un fichier est chargé, il peut être importé ultérieurement pour être utilisé par le système.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-205">Once a file is uploaded it can later be imported to be used by the system.</span></span>

<span data-ttu-id="ee3fe-206">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-206">Parameters</span></span>
* <span data-ttu-id="ee3fe-207">fichier : nom du fichier à charger.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-207">file: Name of the file to upload.</span></span>

<span data-ttu-id="ee3fe-208">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ee3fe-208">Example:</span></span>
```
var form_data = new FormData();
form_data.append("file", file_data);

$.ajax({
    url: "/api/holographic/mapmanager/upload",
    dataType: 'json',
    cache: false,
    contentType: false,
    processData: false,
    data: form_data,
    type: 'post'
})
```

<span data-ttu-id="ee3fe-209">**/API/Holographic/mapmanager/Delete (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-209">**/api/holographic/mapmanager/delete (POST)**</span></span>

<span data-ttu-id="ee3fe-210">Supprime un fichier de base de données de carte, d’ancrage ou de reconstruction spatiale.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-210">Deletes a map, anchor, or spatial reconstruction database file.</span></span> <span data-ttu-id="ee3fe-211">Le fichier doit avoir été préalablement téléchargé ou exporté.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-211">The file must have been previously uploaded or exported.</span></span>

<span data-ttu-id="ee3fe-212">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-212">Parameters</span></span>
* <span data-ttu-id="ee3fe-213">FileName : nom du fichier à supprimer.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-213">FileName: Name of file to delete.</span></span>

<span data-ttu-id="ee3fe-214">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ee3fe-214">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/delete?FileName=" + spaceID)
```

### <a name="export"></a><span data-ttu-id="ee3fe-215">Exporter</span><span class="sxs-lookup"><span data-stu-id="ee3fe-215">Export</span></span>

<span data-ttu-id="ee3fe-216">**/API/Holographic/mapmanager/Export (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-216">**/api/holographic/mapmanager/export (POST)**</span></span>

<span data-ttu-id="ee3fe-217">Exporte le mappage actuellement utilisé par le système.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-217">Exports the map currently in use by the system.</span></span> <span data-ttu-id="ee3fe-218">Une fois exportée, elle peut être téléchargée.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-218">Once exported, it can be downloaded.</span></span> 

<span data-ttu-id="ee3fe-219">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ee3fe-219">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/export")
```

<span data-ttu-id="ee3fe-220">**/API/Holographic/mapmanager/exportanchors (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-220">**/api/holographic/mapmanager/exportanchors (POST)**</span></span>

<span data-ttu-id="ee3fe-221">Exporte le mappage actuellement utilisé par le système.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-221">Exports the map currently in use by the system.</span></span> <span data-ttu-id="ee3fe-222">Une fois exportée, elle peut être téléchargée.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-222">Once exported, it can be downloaded.</span></span> <span data-ttu-id="ee3fe-223">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ee3fe-223">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportanchors")
```

<span data-ttu-id="ee3fe-224">**/API/Holographic/mapmanager/exportmapandanchors (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-224">**/api/holographic/mapmanager/exportmapandanchors (POST)**</span></span>

<span data-ttu-id="ee3fe-225">Exporte le mappage et les ancres actuellement utilisés par le système.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-225">Exports the map and anchors currently in use by the system.</span></span> <span data-ttu-id="ee3fe-226">Une fois exportés, ils peuvent être téléchargés.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-226">Once are exported, they can be downloaded.</span></span> <span data-ttu-id="ee3fe-227">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ee3fe-227">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandanchors")
```

<span data-ttu-id="ee3fe-228">**/API/Holographic/mapmanager/exportmapandspatialmappingdb (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-228">**/api/holographic/mapmanager/exportmapandspatialmappingdb (POST)**</span></span>

<span data-ttu-id="ee3fe-229">Exporte le mappage et la base de données de reconstruction spatiale actuellement utilisés par le système.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-229">Exports the map and spatial reconstruction database currently in use by the system.</span></span> <span data-ttu-id="ee3fe-230">Une fois qu’elles sont exportées, elles peuvent être téléchargées.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-230">Once they are exported, they can be downloaded.</span></span> 

<span data-ttu-id="ee3fe-231">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ee3fe-231">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/exportmapandspatialmappingdb")
```

### <a name="import"></a><span data-ttu-id="ee3fe-232">Importer</span><span class="sxs-lookup"><span data-stu-id="ee3fe-232">Import</span></span>

<span data-ttu-id="ee3fe-233">**/API/Holographic/mapmanager/Import (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-233">**/api/holographic/mapmanager/import (POST)**</span></span>

<span data-ttu-id="ee3fe-234">Indique au système le mappage qui doit être utilisé actuellement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-234">Indicates to the system which map should be used be currently used.</span></span> <span data-ttu-id="ee3fe-235">Peut être appelé sur des fichiers qui ont été exportés ou téléchargés.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-235">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="ee3fe-236">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-236">Parameters</span></span>
* <span data-ttu-id="ee3fe-237">Nom de fichier : nom de la carte à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-237">FileName: Name of the map to be used.</span></span> 

<span data-ttu-id="ee3fe-238">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ee3fe-238">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="ee3fe-239">**/API/Holographic/mapmanager/importanchors (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-239">**/api/holographic/mapmanager/importanchors (POST)**</span></span>

<span data-ttu-id="ee3fe-240">Indique au système les ancres à utiliser actuellement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-240">Indicates to the system which anchors should be used be currently used.</span></span> <span data-ttu-id="ee3fe-241">Peut être appelé sur des fichiers qui ont été exportés ou téléchargés.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-241">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="ee3fe-242">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-242">Parameters</span></span>
* <span data-ttu-id="ee3fe-243">Nom de fichier : nom des ancres à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-243">FileName: Name of the anchors to be used.</span></span> 

<span data-ttu-id="ee3fe-244">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ee3fe-244">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

<span data-ttu-id="ee3fe-245">**/API/Holographic/mapmanager/importspatialmappingdb (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-245">**/api/holographic/mapmanager/importspatialmappingdb (POST)**</span></span>

<span data-ttu-id="ee3fe-246">Indique au système la base de données de reconstruction spatiale à utiliser actuellement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-246">Indicates to the system which spatial reconstruction database should be used be currently used.</span></span> <span data-ttu-id="ee3fe-247">Peut être appelé sur des fichiers qui ont été exportés ou téléchargés.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-247">Can be called on files that have been exported or uploaded.</span></span>

<span data-ttu-id="ee3fe-248">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-248">Parameters</span></span>
* <span data-ttu-id="ee3fe-249">Nom de fichier : nom de la base de connaissances de mappage spatiale à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-249">FileName: Name of the spatial mapping db to be used.</span></span> 

<span data-ttu-id="ee3fe-250">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ee3fe-250">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/import?FileName=" + spaceID, function() { alert("Import was successful!"); })
```

### <a name="other"></a><span data-ttu-id="ee3fe-251">Autre</span><span class="sxs-lookup"><span data-stu-id="ee3fe-251">Other</span></span>

<span data-ttu-id="ee3fe-252">**/API/Holographic/mapmanager/resetmapandanchorsandsrdb (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-252">**/api/holographic/mapmanager/resetmapandanchorsandsrdb (POST)**</span></span>

<span data-ttu-id="ee3fe-253">Réinitialisez le système pour la carte, les ancres et la base de données de reconstruction spatiale.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-253">Reset the system the map, anchors and spatial reconstruction database.</span></span>

<span data-ttu-id="ee3fe-254">Exemple :</span><span class="sxs-lookup"><span data-stu-id="ee3fe-254">Example:</span></span> 
```
$.post("/api/holographic/mapmanager/resetmapandanchorsandsrdb")
```

<span data-ttu-id="ee3fe-255">**/API/Holographic/mapmanager/Status (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-255">**/api/holographic/mapmanager/status (GET)**</span></span>

<span data-ttu-id="ee3fe-256">Obtient l’état du système, notamment les fichiers de base de données de mappage, d’ancrage et de reconstruction spatiale qui ont été importés pour la dernière fois.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-256">Gets the status of the system, including which map, anchors, and spatial reconstruction database files that were last imported.</span></span> 


## <a name="mixed-reality-capture"></a><span data-ttu-id="ee3fe-257">MRC (Mixed Reality Capture)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-257">Mixed Reality Capture</span></span>

<span data-ttu-id="ee3fe-258">**/API/Holographic/MRC/file (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-258">**/api/holographic/mrc/file (GET)**</span></span>

<span data-ttu-id="ee3fe-259">Télécharge un fichier de réalité mixte à partir de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-259">Downloads a mixed reality file from the device.</span></span> <span data-ttu-id="ee3fe-260">Utilisez le paramètre de requête op = Stream pour la diffusion en continu.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-260">Use op=stream query parameter for streaming.</span></span>

<span data-ttu-id="ee3fe-261">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-261">Parameters</span></span>
* <span data-ttu-id="ee3fe-262">nom de fichier : nom, hex64 encodé, du fichier vidéo à récupérer</span><span class="sxs-lookup"><span data-stu-id="ee3fe-262">filename : Name, hex64 encoded, of the video file to get</span></span>
* <span data-ttu-id="ee3fe-263">OP : flux</span><span class="sxs-lookup"><span data-stu-id="ee3fe-263">op : stream</span></span>

<span data-ttu-id="ee3fe-264">**/API/Holographic/MRC/file (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-264">**/api/holographic/mrc/file (DELETE)**</span></span>

<span data-ttu-id="ee3fe-265">Supprime un enregistrement de la réalité mixte de l’appareil.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-265">Deletes a mixed reality recording from the device.</span></span>

<span data-ttu-id="ee3fe-266">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-266">Parameters</span></span>
* <span data-ttu-id="ee3fe-267">nom de fichier : nom, hex64 encodé, du fichier à supprimer</span><span class="sxs-lookup"><span data-stu-id="ee3fe-267">filename : Name, hex64 encoded, of the file to delete</span></span>

<span data-ttu-id="ee3fe-268">**/API/Holographic/MRC/Files (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-268">**/api/holographic/mrc/files (GET)**</span></span>

<span data-ttu-id="ee3fe-269">Retourne la liste des fichiers de réalité mixte stockés sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="ee3fe-269">Returns the list of mixed reality files stored on the device</span></span>

<span data-ttu-id="ee3fe-270">**/API/Holographic/MRC/photo (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-270">**/api/holographic/mrc/photo (POST)**</span></span>

<span data-ttu-id="ee3fe-271">Prend une photo de réalité mixte et crée un fichier sur l’appareil</span><span class="sxs-lookup"><span data-stu-id="ee3fe-271">Takes a mixed reality photo and creates a file on the device</span></span>

<span data-ttu-id="ee3fe-272">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-272">Parameters</span></span>
* <span data-ttu-id="ee3fe-273">Holo : capturer les hologrammes : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-273">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="ee3fe-274">PV : capturer l’appareil photo PV : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-274">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="ee3fe-275">RenderFromCamera : (HoloLens 2 uniquement) rendu du point de vue de la caméra photo/vidéo : true ou false (true par défaut)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-275">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>

<span data-ttu-id="ee3fe-276">**/API/Holographic/MRC/Settings (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-276">**/api/holographic/mrc/settings (GET)**</span></span>

<span data-ttu-id="ee3fe-277">Obtient les paramètres de capture de la réalité mixte par défaut</span><span class="sxs-lookup"><span data-stu-id="ee3fe-277">Gets the default mixed reality capture settings</span></span>

<span data-ttu-id="ee3fe-278">**/API/Holographic/MRC/Settings (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-278">**/api/holographic/mrc/settings (POST)**</span></span>

<span data-ttu-id="ee3fe-279">Définit les paramètres de capture de la réalité mixte par défaut.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-279">Sets the default mixed reality capture settings.</span></span>  <span data-ttu-id="ee3fe-280">Certains de ces paramètres sont appliqués à la photo et à la capture de vidéo MRC du système.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-280">Some of these settings are applied to the system's MRC photo and video capture.</span></span>

<span data-ttu-id="ee3fe-281">**/API/Holographic/MRC/Status (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-281">**/api/holographic/mrc/status (GET)**</span></span>

<span data-ttu-id="ee3fe-282">Obtient l’état de capture de la réalité mixte dans le portail de périphériques Windows.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-282">Gets the state of mixed reality capture within the Windows Device Portal.</span></span>

<span data-ttu-id="ee3fe-283">\**_Réponse_* _</span><span class="sxs-lookup"><span data-stu-id="ee3fe-283">\**_Response_* _</span></span>

<span data-ttu-id="ee3fe-284">La réponse contient une propriété JSON indiquant si le portail de périphériques Windows enregistre ou non une vidéo.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-284">The response contains a JSON property indicating if Windows Device Portal is recording video or not.</span></span>

``` javascript
{"IsRecording" : boolean}
```

<span data-ttu-id="ee3fe-285">_ */API/Holographic/MRC/thumbnail (récupération)*\*</span><span class="sxs-lookup"><span data-stu-id="ee3fe-285">_ */api/holographic/mrc/thumbnail (GET)*\*</span></span>

<span data-ttu-id="ee3fe-286">Obtient l’image miniature pour le fichier spécifié.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-286">Gets the thumbnail image for the specified file.</span></span>

<span data-ttu-id="ee3fe-287">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-287">Parameters</span></span>
* <span data-ttu-id="ee3fe-288">nom de fichier : nom, hex64 encodé, du fichier pour lequel la miniature est demandée.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-288">filename: Name, hex64 encoded, of the file for which the thumbnail is being requested</span></span>

<span data-ttu-id="ee3fe-289">**/API/Holographic/MRC/Video/Control/Start (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-289">**/api/holographic/mrc/video/control/start (POST)**</span></span>

<span data-ttu-id="ee3fe-290">Démarre un enregistrement de la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="ee3fe-290">Starts a mixed reality recording</span></span>

<span data-ttu-id="ee3fe-291">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-291">Parameters</span></span>
* <span data-ttu-id="ee3fe-292">Holo : capturer les hologrammes : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-292">holo : capture holograms: true or false (defaults to false)</span></span>
* <span data-ttu-id="ee3fe-293">PV : capturer l’appareil photo PV : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-293">pv : capture PV camera: true or false (defaults to false)</span></span>
* <span data-ttu-id="ee3fe-294">MIC : capturer le microphone : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-294">mic : capture microphone: true or false (defaults to false)</span></span>
* <span data-ttu-id="ee3fe-295">loopback : capturer l’audio de l’application : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-295">loopback : capture app audio: true or false (defaults to false)</span></span>
* <span data-ttu-id="ee3fe-296">RenderFromCamera : (HoloLens 2 uniquement) rendu du point de vue de la caméra photo/vidéo : true ou false (true par défaut)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-296">RenderFromCamera : (HoloLens 2 only) render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="ee3fe-297">Vstab : (HoloLens 2 uniquement) activer la stabilisation vidéo : true ou false (true par défaut)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-297">vstab : (HoloLens 2 only) enable video stabilization: true or false (defaults to true)</span></span>
* <span data-ttu-id="ee3fe-298">vstabbuffer : (HoloLens 2 uniquement) latence de la mémoire tampon de stabilisation vidéo : de 0 à 30 frames (15 images par défaut)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-298">vstabbuffer: (HoloLens 2 only) video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="ee3fe-299">**/API/Holographic/MRC/Video/Control/Stop (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-299">**/api/holographic/mrc/video/control/stop (POST)**</span></span>

<span data-ttu-id="ee3fe-300">Arrête l’enregistrement de la réalité mixte actuelle</span><span class="sxs-lookup"><span data-stu-id="ee3fe-300">Stops the current mixed reality recording</span></span>

## <a name="mixed-reality-streaming"></a><span data-ttu-id="ee3fe-301">Diffusion en continu de la réalité mixte</span><span class="sxs-lookup"><span data-stu-id="ee3fe-301">Mixed Reality Streaming</span></span>

> [!CAUTION]
> <span data-ttu-id="ee3fe-302">En raison de l’isolement de bouclage, vous ne pouvez pas vous connecter à la réalité mixte en continu à partir d’une application sur un appareil.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-302">Because of loopback isolation, you can't connect to Mixed Reality Streaming from inside an app on a device.</span></span>

<span data-ttu-id="ee3fe-303">HoloLens prend en charge l’aperçu instantané de la réalité mixte via le téléchargement segmenté d’un MP4 fragmenté.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-303">HoloLens supports live preview of mixed reality via chunked download of a fragmented mp4.</span></span>

<span data-ttu-id="ee3fe-304">Les flux de réalité mixte partagent le même ensemble de paramètres pour contrôler ce qui est capturé :</span><span class="sxs-lookup"><span data-stu-id="ee3fe-304">Mixed reality streams share the same set of parameters to control what is captured:</span></span>
* <span data-ttu-id="ee3fe-305">Holo : capturer les hologrammes : true ou false</span><span class="sxs-lookup"><span data-stu-id="ee3fe-305">holo : capture holograms: true or false</span></span>
* <span data-ttu-id="ee3fe-306">PV : capturer l’appareil photo PV : true ou false</span><span class="sxs-lookup"><span data-stu-id="ee3fe-306">pv : capture PV camera: true or false</span></span>
* <span data-ttu-id="ee3fe-307">MIC : capturer le microphone : true ou false</span><span class="sxs-lookup"><span data-stu-id="ee3fe-307">mic : capture microphone: true or false</span></span>
* <span data-ttu-id="ee3fe-308">loopback : capturer l’audio de l’application : true ou false</span><span class="sxs-lookup"><span data-stu-id="ee3fe-308">loopback : capture app audio: true or false</span></span>

<span data-ttu-id="ee3fe-309">Si aucun de ces éléments n’est spécifié : les hologrammes, la caméra photo/vidéo et l’audio de l’application sont capturés</span><span class="sxs-lookup"><span data-stu-id="ee3fe-309">If none of these are specified: holograms, photo/video camera, and app audio will be captured</span></span><br>
<span data-ttu-id="ee3fe-310">Si des paramètres sont spécifiés : les paramètres non spécifiés ont par défaut la valeur false</span><span class="sxs-lookup"><span data-stu-id="ee3fe-310">If any are specified: the unspecified parameters will default to false</span></span>

<span data-ttu-id="ee3fe-311">Paramètres facultatifs (HoloLens 2 uniquement)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-311">Optional parameters (HoloLens 2 only)</span></span>
* <span data-ttu-id="ee3fe-312">RenderFromCamera : rendu du point de vue de la caméra photo/vidéo : true ou false (true par défaut)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-312">RenderFromCamera : render from perspective of photo/video camera: true or false (defaults to true)</span></span>
* <span data-ttu-id="ee3fe-313">Vstab : activer la stabilisation vidéo : true ou false (false par défaut)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-313">vstab : enable video stabilization: true or false (defaults to false)</span></span>
* <span data-ttu-id="ee3fe-314">vstabbuffer : latence de la mémoire tampon de stabilisation vidéo : de 0 à 30 frames (15 images par défaut)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-314">vstabbuffer: video stabilization buffer latency: 0 to 30 frames (defaults to 15 frames)</span></span>

<span data-ttu-id="ee3fe-315">**/API/Holographic/Stream/live.mp4 (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-315">**/api/holographic/stream/live.mp4 (GET)**</span></span>

<span data-ttu-id="ee3fe-316">Un flux 1280x720p 30fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-316">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="ee3fe-317">**/API/Holographic/Stream/live_high.mp4 (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-317">**/api/holographic/stream/live_high.mp4 (GET)**</span></span>

<span data-ttu-id="ee3fe-318">Un flux 1280x720p 30fps 5Mbit.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-318">A 1280x720p 30fps 5Mbit stream.</span></span>

<span data-ttu-id="ee3fe-319">**/API/Holographic/Stream/live_med.mp4 (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-319">**/api/holographic/stream/live_med.mp4 (GET)**</span></span>

<span data-ttu-id="ee3fe-320">Flux 854x480p 30fps 2,5 Mbits.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-320">A 854x480p 30fps 2.5Mbit stream.</span></span>

<span data-ttu-id="ee3fe-321">**/API/Holographic/Stream/live_low.mp4 (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-321">**/api/holographic/stream/live_low.mp4 (GET)**</span></span>

<span data-ttu-id="ee3fe-322">Flux 428x240p 15fps 0,6 Mbit.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-322">A 428x240p 15fps 0.6Mbit stream.</span></span>

## <a name="networking"></a><span data-ttu-id="ee3fe-323">Mise en réseau</span><span class="sxs-lookup"><span data-stu-id="ee3fe-323">Networking</span></span>

<span data-ttu-id="ee3fe-324">**/API/Networking/ipconfig (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-324">**/api/networking/ipconfig (GET)**</span></span>

<span data-ttu-id="ee3fe-325">Obtient la configuration IP actuelle</span><span class="sxs-lookup"><span data-stu-id="ee3fe-325">Gets the current ip configuration</span></span>

## <a name="os-information"></a><span data-ttu-id="ee3fe-326">Informations sur le système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="ee3fe-326">OS Information</span></span>

<span data-ttu-id="ee3fe-327">**/API/OS/info (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-327">**/api/os/info (GET)**</span></span>

<span data-ttu-id="ee3fe-328">Obtient des informations sur le système d’exploitation</span><span class="sxs-lookup"><span data-stu-id="ee3fe-328">Gets operating system information</span></span>

<span data-ttu-id="ee3fe-329">**/API/OS/MachineName (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-329">**/api/os/machinename (GET)**</span></span>

<span data-ttu-id="ee3fe-330">Obtient le nom de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="ee3fe-330">Gets the machine name</span></span>

<span data-ttu-id="ee3fe-331">**/API/OS/MachineName (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-331">**/api/os/machinename (POST)**</span></span>

<span data-ttu-id="ee3fe-332">Définit le nom de l’ordinateur</span><span class="sxs-lookup"><span data-stu-id="ee3fe-332">Sets the machine name</span></span>

<span data-ttu-id="ee3fe-333">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-333">Parameters</span></span>
* <span data-ttu-id="ee3fe-334">nom : nouveau nom de l’ordinateur, hex64 encodé, à affecter à</span><span class="sxs-lookup"><span data-stu-id="ee3fe-334">name : New machine name, hex64 encoded, to set to</span></span>

## <a name="perception-simulation-control"></a><span data-ttu-id="ee3fe-335">Contrôle de simulation de perception</span><span class="sxs-lookup"><span data-stu-id="ee3fe-335">Perception Simulation Control</span></span>

<span data-ttu-id="ee3fe-336">**/API/Holographic/simulation/Control/mode (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-336">**/api/holographic/simulation/control/mode (GET)**</span></span>

<span data-ttu-id="ee3fe-337">Obtient le mode de simulation</span><span class="sxs-lookup"><span data-stu-id="ee3fe-337">Get the simulation mode</span></span>

<span data-ttu-id="ee3fe-338">**/API/Holographic/simulation/Control/mode (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-338">**/api/holographic/simulation/control/mode (POST)**</span></span>

<span data-ttu-id="ee3fe-339">Définir le mode de simulation</span><span class="sxs-lookup"><span data-stu-id="ee3fe-339">Set the simulation mode</span></span>

<span data-ttu-id="ee3fe-340">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-340">Parameters</span></span>
* <span data-ttu-id="ee3fe-341">mode : mode de simulation : par défaut, simulation, distant, hérité</span><span class="sxs-lookup"><span data-stu-id="ee3fe-341">mode : simulation mode: default, simulation, remote, legacy</span></span>

<span data-ttu-id="ee3fe-342">**/API/Holographic/simulation/Control/Stream (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-342">**/api/holographic/simulation/control/stream (DELETE)**</span></span>

<span data-ttu-id="ee3fe-343">Supprimer un flux de contrôle.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-343">Delete a control stream.</span></span>

<span data-ttu-id="ee3fe-344">**/API/Holographic/simulation/Control/Stream (obtient/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-344">**/api/holographic/simulation/control/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="ee3fe-345">Ouvrez une connexion de socket Web pour un flux de contrôle.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-345">Open a web socket connection for a control stream.</span></span>

<span data-ttu-id="ee3fe-346">**/API/Holographic/simulation/Control/Stream (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-346">**/api/holographic/simulation/control/stream (POST)**</span></span>

<span data-ttu-id="ee3fe-347">Créez un flux de contrôle (priorité obligatoire) ou publiez des données dans un flux créé (streamId requis).</span><span class="sxs-lookup"><span data-stu-id="ee3fe-347">Create a control stream (priority is required) or post data to a created stream (streamId required).</span></span> <span data-ttu-id="ee3fe-348">Les données publiées sont supposées être de type « application/octet-stream ».</span><span class="sxs-lookup"><span data-stu-id="ee3fe-348">Posted data is expected to be of type 'application/octet-stream'.</span></span>

<span data-ttu-id="ee3fe-349">**/API/Holographic/Simulation/Display/Stream (obtient/WebSocket)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-349">**/api/holographic/simulation/display/stream (GET/WebSocket)**</span></span>

<span data-ttu-id="ee3fe-350">Demandez un flux vidéo de simulation contenant le contenu affiché sur le système lorsqu’il est en mode « simulation ».</span><span class="sxs-lookup"><span data-stu-id="ee3fe-350">Request a simulation video stream containing the content rendered to the system display when in 'Simulation' mode.</span></span>  <span data-ttu-id="ee3fe-351">Un en-tête de descripteur de format simple sera envoyé initialement, suivi des textures encodées H. 264, chacune précédée d’un en-tête indiquant l’index oculaire et la taille de la texture.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-351">A simple format descriptor header will be sent initially, followed by H.264-encoded textures, each preceded by a header indicating the eye index and texture size.</span></span>

## <a name="perception-simulation-playback"></a><span data-ttu-id="ee3fe-352">Lecture de simulation de perception</span><span class="sxs-lookup"><span data-stu-id="ee3fe-352">Perception Simulation Playback</span></span>

<span data-ttu-id="ee3fe-353">**/API/Holographic/simulation/playback/file (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-353">**/api/holographic/simulation/playback/file (DELETE)**</span></span>

<span data-ttu-id="ee3fe-354">Supprimer un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-354">Delete a recording.</span></span>

<span data-ttu-id="ee3fe-355">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-355">Parameters</span></span>
* <span data-ttu-id="ee3fe-356">enregistrement : nom de l’enregistrement à supprimer.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-356">recording : Name of recording to delete.</span></span>

<span data-ttu-id="ee3fe-357">**/API/Holographic/simulation/playback/file (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-357">**/api/holographic/simulation/playback/file (POST)**</span></span>

<span data-ttu-id="ee3fe-358">Télécharger un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-358">Upload a recording.</span></span>

<span data-ttu-id="ee3fe-359">**/API/Holographic/simulation/playback/Files (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-359">**/api/holographic/simulation/playback/files (GET)**</span></span>

<span data-ttu-id="ee3fe-360">Récupération de tous les enregistrements.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-360">Get all recordings.</span></span>

<span data-ttu-id="ee3fe-361">**/API/Holographic/simulation/playback/session (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-361">**/api/holographic/simulation/playback/session (GET)**</span></span>

<span data-ttu-id="ee3fe-362">Obtient l’état de lecture actuel d’un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-362">Get the current playback state of a recording.</span></span>

<span data-ttu-id="ee3fe-363">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-363">Parameters</span></span>
* <span data-ttu-id="ee3fe-364">enregistrement : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-364">recording : Name of recording.</span></span>

<span data-ttu-id="ee3fe-365">**/API/Holographic/simulation/playback/session/file (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-365">**/api/holographic/simulation/playback/session/file (DELETE)**</span></span>

<span data-ttu-id="ee3fe-366">Décharger un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-366">Unload a recording.</span></span>

<span data-ttu-id="ee3fe-367">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-367">Parameters</span></span>
* <span data-ttu-id="ee3fe-368">enregistrement : nom de l’enregistrement à décharger.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-368">recording : Name of recording to unload.</span></span>

<span data-ttu-id="ee3fe-369">**/API/Holographic/simulation/playback/session/file (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-369">**/api/holographic/simulation/playback/session/file (POST)**</span></span>

<span data-ttu-id="ee3fe-370">Charger un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-370">Load a recording.</span></span>

<span data-ttu-id="ee3fe-371">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-371">Parameters</span></span>
* <span data-ttu-id="ee3fe-372">enregistrement : nom de l’enregistrement à charger.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-372">recording : Name of recording to load.</span></span>

<span data-ttu-id="ee3fe-373">**/API/Holographic/simulation/playback/session/Files (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-373">**/api/holographic/simulation/playback/session/files (GET)**</span></span>

<span data-ttu-id="ee3fe-374">Récupération de tous les enregistrements chargés.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-374">Get all loaded recordings.</span></span>

<span data-ttu-id="ee3fe-375">**/API/Holographic/simulation/playback/session/pause (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-375">**/api/holographic/simulation/playback/session/pause (POST)**</span></span>

<span data-ttu-id="ee3fe-376">Suspendre un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-376">Pause a recording.</span></span>

<span data-ttu-id="ee3fe-377">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-377">Parameters</span></span>
* <span data-ttu-id="ee3fe-378">enregistrement : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-378">recording : Name of recording.</span></span>

<span data-ttu-id="ee3fe-379">**/API/Holographic/simulation/playback/session/Play (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-379">**/api/holographic/simulation/playback/session/play (POST)**</span></span>

<span data-ttu-id="ee3fe-380">Lire un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-380">Play a recording.</span></span>

<span data-ttu-id="ee3fe-381">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-381">Parameters</span></span>
* <span data-ttu-id="ee3fe-382">enregistrement : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-382">recording : Name of recording.</span></span>

<span data-ttu-id="ee3fe-383">**/API/Holographic/simulation/playback/session/Stop (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-383">**/api/holographic/simulation/playback/session/stop (POST)**</span></span>

<span data-ttu-id="ee3fe-384">Arrêter un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-384">Stop a recording.</span></span>

<span data-ttu-id="ee3fe-385">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-385">Parameters</span></span>
* <span data-ttu-id="ee3fe-386">enregistrement : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-386">recording : Name of recording.</span></span>

<span data-ttu-id="ee3fe-387">**/API/Holographic/simulation/playback/session/types (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-387">**/api/holographic/simulation/playback/session/types (GET)**</span></span>

<span data-ttu-id="ee3fe-388">Obtenir les types de données dans un enregistrement chargé.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-388">Get the types of data in a loaded recording.</span></span>

<span data-ttu-id="ee3fe-389">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-389">Parameters</span></span>
* <span data-ttu-id="ee3fe-390">enregistrement : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-390">recording : Name of recording.</span></span>

## <a name="perception-simulation-recording"></a><span data-ttu-id="ee3fe-391">Enregistrement de simulation de perception</span><span class="sxs-lookup"><span data-stu-id="ee3fe-391">Perception Simulation Recording</span></span>

<span data-ttu-id="ee3fe-392">**/API/Holographic/simulation/Recording/Start (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-392">**/api/holographic/simulation/recording/start (POST)**</span></span>

<span data-ttu-id="ee3fe-393">Démarrez un enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-393">Start a recording.</span></span> <span data-ttu-id="ee3fe-394">Un seul enregistrement peut être actif à la fois.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-394">Only a single recording can be active at once.</span></span> <span data-ttu-id="ee3fe-395">Vous devez définir l’un des principaux, mains, spatialMapping ou environnement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-395">One of head, hands, spatialMapping or environment must be set.</span></span>

<span data-ttu-id="ee3fe-396">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-396">Parameters</span></span>
* <span data-ttu-id="ee3fe-397">Head : définissez sur 1 pour enregistrer les données de tête.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-397">head : Set to 1 to record head data.</span></span>
* <span data-ttu-id="ee3fe-398">mains : définissez sur 1 pour enregistrer les données de la main.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-398">hands : Set to 1 to record hand data.</span></span>
* <span data-ttu-id="ee3fe-399">spatialMapping : affectez la valeur 1 pour enregistrer le mappage spatial.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-399">spatialMapping : Set to 1 to record spatial mapping.</span></span>
* <span data-ttu-id="ee3fe-400">environnement : définissez sur 1 pour enregistrer les données d’environnement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-400">environment : Set to 1 to record environment data.</span></span>
* <span data-ttu-id="ee3fe-401">nom : nom de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-401">name : Name of the recording.</span></span>
* <span data-ttu-id="ee3fe-402">singleSpatialMappingFrame : affectez la valeur 1 pour enregistrer uniquement un seul frame de mappage spatial.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-402">singleSpatialMappingFrame : Set to 1 to record only a single spatial mapping frame.</span></span>

<span data-ttu-id="ee3fe-403">**/API/Holographic/simulation/Recording/Status (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-403">**/api/holographic/simulation/recording/status (GET)**</span></span>

<span data-ttu-id="ee3fe-404">Obtient l’état de l’enregistrement.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-404">Get recording state.</span></span>

<span data-ttu-id="ee3fe-405">**/API/Holographic/simulation/Recording/Stop (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-405">**/api/holographic/simulation/recording/stop (GET)**</span></span>

<span data-ttu-id="ee3fe-406">Arrêter l’enregistrement en cours.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-406">Stop the current recording.</span></span> <span data-ttu-id="ee3fe-407">L’enregistrement est retourné sous la forme d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-407">Recording will be returned as a file.</span></span>

## <a name="performance-data"></a><span data-ttu-id="ee3fe-408">Données de performances</span><span class="sxs-lookup"><span data-stu-id="ee3fe-408">Performance data</span></span>

<span data-ttu-id="ee3fe-409">**/API/ResourceManager/Processes (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-409">**/api/resourcemanager/processes (GET)**</span></span>

<span data-ttu-id="ee3fe-410">Retourne la liste des processus en cours d’exécution avec les détails</span><span class="sxs-lookup"><span data-stu-id="ee3fe-410">Returns the list of running processes with details</span></span>

<span data-ttu-id="ee3fe-411">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="ee3fe-411">Return data</span></span>
* <span data-ttu-id="ee3fe-412">JSON avec liste de processus et détails pour chaque processus</span><span class="sxs-lookup"><span data-stu-id="ee3fe-412">JSON with list of processes and details for each process</span></span>

<span data-ttu-id="ee3fe-413">**/API/ResourceManager/systemperf (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-413">**/api/resourcemanager/systemperf (GET)**</span></span>

<span data-ttu-id="ee3fe-414">Retourne les statistiques de performances système (lecture/écriture d’e/s, statistiques de mémoire, etc.).</span><span class="sxs-lookup"><span data-stu-id="ee3fe-414">Returns system perf statistics (I/O read/write, memory stats etc.</span></span>

<span data-ttu-id="ee3fe-415">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="ee3fe-415">Return data</span></span>
* <span data-ttu-id="ee3fe-416">JSON avec informations système : processeur, GPU, mémoire, réseau, e/s</span><span class="sxs-lookup"><span data-stu-id="ee3fe-416">JSON with system information: CPU, GPU, Memory, Network, IO</span></span>

## <a name="power"></a><span data-ttu-id="ee3fe-417">Power</span><span class="sxs-lookup"><span data-stu-id="ee3fe-417">Power</span></span>

<span data-ttu-id="ee3fe-418">**/API/Power/Battery (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-418">**/api/power/battery (GET)**</span></span>

<span data-ttu-id="ee3fe-419">Obtient l’état actuel de la batterie</span><span class="sxs-lookup"><span data-stu-id="ee3fe-419">Gets the current battery state</span></span>

<span data-ttu-id="ee3fe-420">**/API/Power/State (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-420">**/api/power/state (GET)**</span></span>

<span data-ttu-id="ee3fe-421">Vérifie si le système est dans un état de faible consommation d’énergie.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-421">Checks if the system is in a low power state</span></span>

## <a name="remote-control"></a><span data-ttu-id="ee3fe-422">Contrôle à distance</span><span class="sxs-lookup"><span data-stu-id="ee3fe-422">Remote Control</span></span>

<span data-ttu-id="ee3fe-423">**/API/Control/Restart (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-423">**/api/control/restart (POST)**</span></span>

<span data-ttu-id="ee3fe-424">Redémarre l’appareil cible</span><span class="sxs-lookup"><span data-stu-id="ee3fe-424">Restarts the target device</span></span>

<span data-ttu-id="ee3fe-425">**/API/Control/Shutdown (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-425">**/api/control/shutdown (POST)**</span></span>

<span data-ttu-id="ee3fe-426">Arrête l’appareil cible</span><span class="sxs-lookup"><span data-stu-id="ee3fe-426">Shuts down the target device</span></span>

## <a name="task-manager"></a><span data-ttu-id="ee3fe-427">Gestionnaire des tâches</span><span class="sxs-lookup"><span data-stu-id="ee3fe-427">Task Manager</span></span>

<span data-ttu-id="ee3fe-428">**/API/taskmanager/App (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-428">**/api/taskmanager/app (DELETE)**</span></span>

<span data-ttu-id="ee3fe-429">Arrête une application moderne</span><span class="sxs-lookup"><span data-stu-id="ee3fe-429">Stops a modern app</span></span>

<span data-ttu-id="ee3fe-430">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-430">Parameters</span></span>
* <span data-ttu-id="ee3fe-431">Package : nom complet du package d’application, hex64 encodé</span><span class="sxs-lookup"><span data-stu-id="ee3fe-431">package : Full name of the app package, hex64 encoded</span></span>
* <span data-ttu-id="ee3fe-432">forceStop : force l’arrêt de tous les processus (= oui)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-432">forcestop : Force all processes to stop (=yes)</span></span>

<span data-ttu-id="ee3fe-433">**/API/taskmanager/App (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-433">**/api/taskmanager/app (POST)**</span></span>

<span data-ttu-id="ee3fe-434">Démarre une application moderne</span><span class="sxs-lookup"><span data-stu-id="ee3fe-434">Starts a modern app</span></span>

<span data-ttu-id="ee3fe-435">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-435">Parameters</span></span>
* <span data-ttu-id="ee3fe-436">AppID : PRAID de l’application à démarrer, hex64 encodé</span><span class="sxs-lookup"><span data-stu-id="ee3fe-436">appid : PRAID of app to start, hex64 encoded</span></span>
* <span data-ttu-id="ee3fe-437">Package : nom complet du package d’application, hex64 encodé</span><span class="sxs-lookup"><span data-stu-id="ee3fe-437">package : Full name of the app package, hex64 encoded</span></span>

## <a name="wifi-management"></a><span data-ttu-id="ee3fe-438">Gestion WiFi</span><span class="sxs-lookup"><span data-stu-id="ee3fe-438">WiFi Management</span></span>

<span data-ttu-id="ee3fe-439">**/API/WiFi/interfaces (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-439">**/api/wifi/interfaces (GET)**</span></span>

<span data-ttu-id="ee3fe-440">Énumère les interfaces de réseau sans fil</span><span class="sxs-lookup"><span data-stu-id="ee3fe-440">Enumerates wireless network interfaces</span></span>

<span data-ttu-id="ee3fe-441">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="ee3fe-441">Return data</span></span>
* <span data-ttu-id="ee3fe-442">Liste des interfaces sans fil avec des détails (GUID, description, etc.)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-442">List of wireless interfaces with details (GUID, description etc.)</span></span>

<span data-ttu-id="ee3fe-443">**/API/WiFi/Network (supprimer)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-443">**/api/wifi/network (DELETE)**</span></span>

<span data-ttu-id="ee3fe-444">Supprime un profil associé à un réseau sur une interface spécifiée</span><span class="sxs-lookup"><span data-stu-id="ee3fe-444">Deletes a profile associated with a network on a specified interface</span></span>

<span data-ttu-id="ee3fe-445">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-445">Parameters</span></span>
* <span data-ttu-id="ee3fe-446">Interface : GUID de l’interface réseau</span><span class="sxs-lookup"><span data-stu-id="ee3fe-446">interface : network interface guid</span></span>
* <span data-ttu-id="ee3fe-447">Profil : nom du profil</span><span class="sxs-lookup"><span data-stu-id="ee3fe-447">profile : profile name</span></span>

<span data-ttu-id="ee3fe-448">**/API/WiFi/Networks (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-448">**/api/wifi/networks (GET)**</span></span>

<span data-ttu-id="ee3fe-449">Énumère les réseaux sans fil sur l’interface réseau spécifiée.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-449">Enumerates wireless networks on the specified network interface</span></span>

<span data-ttu-id="ee3fe-450">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-450">Parameters</span></span>
* <span data-ttu-id="ee3fe-451">Interface : GUID de l’interface réseau</span><span class="sxs-lookup"><span data-stu-id="ee3fe-451">interface : network interface guid</span></span>

<span data-ttu-id="ee3fe-452">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="ee3fe-452">Return data</span></span>
* <span data-ttu-id="ee3fe-453">Liste des réseaux sans fil détectés sur l’interface réseau avec les détails</span><span class="sxs-lookup"><span data-stu-id="ee3fe-453">List of wireless networks found on the network interface with details</span></span>

<span data-ttu-id="ee3fe-454">**/API/WiFi/Network (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-454">**/api/wifi/network (POST)**</span></span>

<span data-ttu-id="ee3fe-455">Se connecte ou se déconnecte à un réseau sur l’interface spécifiée</span><span class="sxs-lookup"><span data-stu-id="ee3fe-455">Connects or disconnects to a network on the specified interface</span></span>

<span data-ttu-id="ee3fe-456">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-456">Parameters</span></span>
* <span data-ttu-id="ee3fe-457">Interface : GUID de l’interface réseau</span><span class="sxs-lookup"><span data-stu-id="ee3fe-457">interface : network interface guid</span></span>
* <span data-ttu-id="ee3fe-458">SSID : SSID, hex64 encodé, pour se connecter à</span><span class="sxs-lookup"><span data-stu-id="ee3fe-458">ssid : ssid, hex64 encoded, to connect to</span></span>
* <span data-ttu-id="ee3fe-459">opération : se connecter ou se déconnecter</span><span class="sxs-lookup"><span data-stu-id="ee3fe-459">op : connect or disconnect</span></span>
* <span data-ttu-id="ee3fe-460">CreateProfile : oui ou non</span><span class="sxs-lookup"><span data-stu-id="ee3fe-460">createprofile : yes or no</span></span>
* <span data-ttu-id="ee3fe-461">clé : clé partagée, encodée en hex64</span><span class="sxs-lookup"><span data-stu-id="ee3fe-461">key : shared key, hex64 encoded</span></span>

## <a name="windows-performance-recorder"></a><span data-ttu-id="ee3fe-462">Enregistreur de performances Windows</span><span class="sxs-lookup"><span data-stu-id="ee3fe-462">Windows Performance Recorder</span></span>

<span data-ttu-id="ee3fe-463">**/API/WPR/customtrace (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-463">**/api/wpr/customtrace (POST)**</span></span>

<span data-ttu-id="ee3fe-464">Charge un profil WPR et démarre le suivi à l’aide du profil chargé.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-464">Uploads a WPR profile and starts tracing using the uploaded profile.</span></span>

<span data-ttu-id="ee3fe-465">Payload</span><span class="sxs-lookup"><span data-stu-id="ee3fe-465">Payload</span></span>
* <span data-ttu-id="ee3fe-466">corps http en plusieurs parties, conforme</span><span class="sxs-lookup"><span data-stu-id="ee3fe-466">multi-part conforming http body</span></span>

<span data-ttu-id="ee3fe-467">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="ee3fe-467">Return data</span></span>
* <span data-ttu-id="ee3fe-468">Retourne l’état de la session WPR.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-468">Returns the WPR session status.</span></span>

<span data-ttu-id="ee3fe-469">**/API/WPR/Status (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-469">**/api/wpr/status (GET)**</span></span>

<span data-ttu-id="ee3fe-470">Récupère l’état de la session WPR</span><span class="sxs-lookup"><span data-stu-id="ee3fe-470">Retrieves the status of the WPR session</span></span>

<span data-ttu-id="ee3fe-471">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="ee3fe-471">Return data</span></span>
* <span data-ttu-id="ee3fe-472">État de session WPR.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-472">WPR session status.</span></span>

<span data-ttu-id="ee3fe-473">**/API/WPR/trace (récupération)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-473">**/api/wpr/trace (GET)**</span></span>

<span data-ttu-id="ee3fe-474">Arrête une session de suivi WPR (performance)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-474">Stops a WPR (performance) tracing session</span></span>

<span data-ttu-id="ee3fe-475">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="ee3fe-475">Return data</span></span>
* <span data-ttu-id="ee3fe-476">Retourne le fichier ETL de trace</span><span class="sxs-lookup"><span data-stu-id="ee3fe-476">Returns the trace ETL file</span></span>

<span data-ttu-id="ee3fe-477">**/API/WPR/trace (publication)**</span><span class="sxs-lookup"><span data-stu-id="ee3fe-477">**/api/wpr/trace (POST)**</span></span>

<span data-ttu-id="ee3fe-478">Démarre une session de suivi WPR (performance)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-478">Starts a WPR (performance) tracing sessions</span></span>

<span data-ttu-id="ee3fe-479">Paramètres</span><span class="sxs-lookup"><span data-stu-id="ee3fe-479">Parameters</span></span>
* <span data-ttu-id="ee3fe-480">Profil : nom du profil.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-480">profile : Profile name.</span></span> <span data-ttu-id="ee3fe-481">Les profils disponibles sont stockés dans perfprofiles/profiles.jssur</span><span class="sxs-lookup"><span data-stu-id="ee3fe-481">Available profiles are stored in perfprofiles/profiles.json</span></span>

<span data-ttu-id="ee3fe-482">Retourner les données</span><span class="sxs-lookup"><span data-stu-id="ee3fe-482">Return data</span></span>
* <span data-ttu-id="ee3fe-483">Dans Démarrer, retourne l’état de la session WPR.</span><span class="sxs-lookup"><span data-stu-id="ee3fe-483">On start, returns the WPR session status.</span></span>

## <a name="see-also"></a><span data-ttu-id="ee3fe-484">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee3fe-484">See also</span></span>
* [<span data-ttu-id="ee3fe-485">Utilisation du portail d’appareil Windows</span><span class="sxs-lookup"><span data-stu-id="ee3fe-485">Using the Windows Device Portal</span></span>](using-the-windows-device-portal.md)
* [<span data-ttu-id="ee3fe-486">Informations de référence sur l’API principale du portail des appareils (UWP)</span><span class="sxs-lookup"><span data-stu-id="ee3fe-486">Device Portal core API reference (UWP)</span></span>](https://docs.microsoft.com/windows/uwp/debug-test-perf/device-portal-api-core)
