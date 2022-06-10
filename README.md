# Scheduled Monitor

If  you need to generate alerts based on a schedule. Ie. only generate alert of a specific monitor during a certian maintenance window. This maybe required because maintence windows are per objects all the monitors fall under same window. In this case we can schedule per alert.

High Level Steps
1. Copy Monitor Type and if ncessasry related modules from desired mp
1. Copy Unit Monitor Type
1. In the failed regulardetection add the scheduler filter
```Xml
  <ConditionDetection ID="Schedule" TypeID="System!System.SchedulerFilter">
    <SchedulerFilter>
      <ProcessDataMode>OnSchedule</ProcessDataMode>
      <Schedule>
        <WeeklySchedule>
          <Windows>
            <Daily>
              <Start>08:00</Start>
              <End>18:00</End>
              <DaysOfWeekMask>62</DaysOfWeekMask>
            </Daily>
          </Windows>
        </WeeklySchedule>
        <ExcludeDates />
      </Schedule>
      <UseCurrentTime>true</UseCurrentTime>
    </SchedulerFilter>
  </ConditionDetection>
```
1. Copy Alert String resource and Display Strings
1. Update ids and references
