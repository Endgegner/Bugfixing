# Bugfixing
Files to fix

MoreCrashedShipParts.xml (Last attempt with fiddling)

PatchOperationMCSP.xml (Functionable, no errors, but crashed ship parts dont drop/spawn what i want (a Mechanoid Power Cell + other stuff)

This is because it gets overwritten by the parent:

<?xml version="1.0" encoding="utf-8" ?>
<Defs>

  <ThingDef ParentName="BuildingBase" Name="ShipPartBase" Abstract="True">
		<thingClass>Building_CrashedShipPart</thingClass>
		<altitudeLayer>Building</altitudeLayer>
    <pathCost>150</pathCost>
    <blockWind>true</blockWind>
    <passability>Impassable</passability>
    <fillPercent>1.0</fillPercent>
    <size>(6,3)</size>
    <statBases>
      <MaxHitPoints>1000</MaxHitPoints>
      <Flammability>0</Flammability>
      <Beauty>-200</Beauty>
    </statBases>
    <tickerType>Normal</tickerType>
		<leaveResourcesWhenKilled>false</leaveResourcesWhenKilled>
    <killedLeavings>
      <Steel>100</Steel>
      <Plasteel>35</Plasteel>
      <ChunkSlagSteel>8</ChunkSlagSteel>
      <ComponentIndustrial>4</ComponentIndustrial>
      <ComponentSpacer>1</ComponentSpacer>
    </killedLeavings>
    <rotatable>true</rotatable>
    <selectable>true</selectable>
    <neverMultiSelect>true</neverMultiSelect>
    <terrainAffordanceNeeded>Light</terrainAffordanceNeeded>
    <soundImpactDefault>BulletImpact_Metal</soundImpactDefault>
    <drawerType>MapMeshOnly</drawerType>
    <repairEffect>ConstructMetal</repairEffect>
    <forceDebugSpawnable>true</forceDebugSpawnable>
    <building>
			<claimable>false</claimable>
			<soundAmbient>CrashedShipPart_Ambience</soundAmbient>
      <roofCollapseDamageMultiplier>0.2</roofCollapseDamageMultiplier>
    </building>
    <comps>
      <li Class="CompProperties_SnowExpand" />
      <li Class="CompProperties_SpawnerMechanoidsOnDamaged" />
    </comps>
  </ThingDef>

  <ThingDef ParentName="ShipPartBase">
    <defName>CrashedPsychicEmanatorShipPart</defName>
    <label>ship part (psychic)</label>
    <description>A mysterious crashed piece of a spaceship. It may contain any manner of deadly defenders and exotic materials. This one seems to be emanating psychic waves.</description>
    <graphicData>
      <texPath>Things/Building/Exotic/CrashedShipPart</texPath>
      <graphicClass>Graphic_Single</graphicClass>
      <drawSize>(6,3)</drawSize>
			<shadowData>
				<volume>(5.17, 1.0, 2.4)</volume>
        <offset>(-0.16, 0, -0.08)</offset>
			</shadowData>
    </graphicData>
    <comps>
      <li Class="CompProperties_PsychicDrone" />
      <li Class="CompProperties_AnimalInsanityPulser" />
    </comps>
  </ThingDef>

  <ThingDef ParentName="ShipPartBase">
    <defName>CrashedPoisonShipPart</defName>
    <label>ship part (poison)</label>
    <description>A mysterious crashed piece of a spaceship. It may contain any manner of deadly defenders and exotic materials. This one seems to be killing plant life around it.</description>
    <graphicData>
      <texPath>Things/Building/Exotic/CrashedPoisonShipPart</texPath>
      <graphicClass>Graphic_Single</graphicClass>
      <drawSize>(6,3)</drawSize>
			<shadowData>
				<volume>(5.5, 1.0, 2.45)</volume>
			</shadowData>
    </graphicData>
		<comps>
			<li Class="CompProperties_PlantHarmRadius">
				<radiusPerDayCurve>
          <points>
						<li>0,5</li>
						<li>1.5,18</li>
						<li>6,40</li>
						<li>20,100</li>
					</points>
				</radiusPerDayCurve>
				<harmFrequencyPerArea>0.015</harmFrequencyPerArea>
			</li>
		</comps>
  </ThingDef>

	<!-- =============================== Misc ============================ -->
	
  <ThingDef ParentName="BuildingBase">
    <defName>ShipChunk</defName>
    <label>ship chunk</label>
    <description>A chunk of a spacecraft. Can be deconstructed to yield useful resources.</description>
    <category>Building</category>
    <graphicData>
      <texPath>Things/Building/Exotic/ShipChunk</texPath>
      <graphicClass>Graphic_Random</graphicClass>
      <drawSize>(2,2)</drawSize>
      <damageData>
        <rect>(0.1,0.1,1.8,1.8)</rect>
      </damageData>
      <shadowData>
        <volume>(1.39,0.5,1.25)</volume>
      </shadowData>
    </graphicData>
    <altitudeLayer>Building</altitudeLayer>
		<pathCost>35</pathCost>
    <blockWind>true</blockWind>
    <passability>PassThroughOnly</passability>
    <fillPercent>0.50</fillPercent>
    <size>(2,2)</size>
    <statBases>
      <MaxHitPoints>300</MaxHitPoints>
      <Flammability>0</Flammability>
      <Beauty>-20</Beauty>
      <WorkToBuild>12000</WorkToBuild>
    </statBases>
    <leaveResourcesWhenKilled>false</leaveResourcesWhenKilled>
    <killedLeavings>
      <ChunkSlagSteel>2</ChunkSlagSteel>
    </killedLeavings>
    <costList>
      <ComponentIndustrial>11</ComponentIndustrial>
      <Steel>40</Steel>
    </costList>
    <building>
      <claimable>false</claimable>
      <alwaysDeconstructible>true</alwaysDeconstructible>
    </building>
    <selectable>true</selectable>
    <soundImpactDefault>BulletImpact_Metal</soundImpactDefault>
    <drawerType>MapMeshOnly</drawerType>
    <repairEffect>ConstructMetal</repairEffect>
  </ThingDef>

</Defs>
