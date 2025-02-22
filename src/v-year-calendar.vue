<template>
  <div></div>
</template>

<script>
import JsCalendar from '../../js-year-calendar/dist/js-year-calendar';
import '../../js-year-calendar/dist/js-year-calendar.css';

export default {
    name: 'Calendar',
    props: [
        'allowOverlap',
        'alwaysHalfDay',
        'forceFullDayClicks',
        'contextMenuItems',
        'customDayRenderer',
        'customDataSourceRenderer',
        'dataSource',
        'disabledDays',
        'disabledWeekDays',
        'displayDisabledDataSource',
        'displayHeader',
        'displayWeekNumber',
        'enableContextMenu',
        'enableRangeSelection',
        'hiddenWeekDays',
        'language',
        'loadingTemplate',
        'maxDate',
        'minDate',
        'roundRangeLimits',
        'renderStyle',
        'weekStart',
        'startDate',
        'year',
        'months'
    ],
    data: () => ({
        shouldRender: false
    }),
    mounted() {
        this.calendar = new JsCalendar(this.$el, {
            // Options
            allowOverlap: this.allowOverlap,
            alwaysHalfDay: this.alwaysHalfDay,
            forceFullDayClicks: this.forceFullDayClicks,
            contextMenuItems: this.contextMenuItems,
            customDayRenderer: this.customDayRenderer,
            customDataSourceRenderer: this.customDataSourceRenderer,
            dataSource: this.dataSource,
            disabledDays: this.disabledDays,
            disabledWeekDays: this.disabledWeekDays,
            displayDisabledDataSource: this.displayDisabledDataSource,
            displayHeader: this.displayHeader,
            displayWeekNumber: this.displayWeekNumber,
            enableContextMenu: this.enableContextMenu,
            enableRangeSelection: this.enableRangeSelection,
            hiddenWeekDays: this.hiddenWeekDays,
            language: this.language,
            loadingTemplate: this.loadingTemplate,
            maxDate: this.maxDate,
            minDate: this.minDate,
            roundRangeLimits: this.roundRangeLimits,
            style: this.renderStyle,
            weekStart: this.weekStart,
            startDate: this.startDate,
            startYear: this.year,
            numberMonthsDisplayed: this.months,

            // Events
            clickDay: e => this.$emit('click-day', e),
            dayContextMenu: e => this.$emit('day-context-menu', e),
            mouseOnDay: e => this.$emit('mouse-on-day', e),
            mouseOutDay: e => this.$emit('mouse-out-day', e),
            renderEnd: e => this.$emit('render-end', e),
            selectRange: e => this.$emit('select-range', e),
            clearRange: e => this.$emit('clear-range', e),
            yearChanged: e => this.$emit('year-changed', e)
        });
    },
    computed: {
        allProps: function() {
            return `
                ${this.allowOverlap}
                ${this.alwaysHalfDay}
                ${this.forceFullDayClicks}
                ${this.contextMenuItems}
                ${this.customDayRenderer}
                ${this.customDataSourceRenderer}
                ${this.dataSource}
                ${this.disabledDays}
                ${this.disabledWeekDays}
                ${this.displayDisabledDataSource}
                ${this.displayHeader}
                ${this.displayWeekNumber}
                ${this.enableContextMenu}
                ${this.enableRangeSelection}
                ${this.hiddenWeekDays}
                ${this.language}
                ${this.loadingTemplate}
                ${this.maxDate}
                ${this.minDate}
                ${this.roundRangeLimits}
                ${this.renderStyle}
                ${this.weekStart}
                ${this.startDate}
                ${this.year}
                ${this.months}
            `;
        }
    },
    watch: {
        allowOverlap: function(val) { this.calendar.setAllowOverlap(val); },
        alwaysHalfDay: function(val) { this.calendar.setAlwaysHalfDay(val, true); this.shouldRender = true; },
        forceFullDayClicks: function(val) { this.calendar.setForceFullDayClicks(val, true); this.shouldRender = true; },
        contextMenuItems: function(val) { this.calendar.setContextMenuItems(val, true); this.shouldRender = true; },
        customDayRenderer: function(val) { this.calendar.setCustomDayRenderer(val, true); this.shouldRender = true; },
        customDataSourceRenderer: function(val) { this.calendar.setCustomDataSourceRenderer(val, true); this.shouldRender = true; },
        dataSource: function(val) { this.calendar.setDataSource(val, true); this.shouldRender = true; },
        disabledDays: function(val) { this.calendar.setDisabledDays(val, true); this.shouldRender = true; },
        disabledWeekDays: function(val) { this.calendar.setDisabledWeekDays(val, true); this.shouldRender = true; },
        displayDisabledDataSource: function(val) { this.calendar.setDisplayDisabledDataSource(val, true); this.shouldRender = true; },
        displayHeader: function(val) { this.calendar.setDisplayHeader(val, true); this.shouldRender = true; },
        displayWeekNumber: function(val) { this.calendar.setDisplayWeekNumber(val, true); this.shouldRender = true; },
        enableContextMenu: function(val) { this.calendar.setEnableContextMenu(val, true); this.shouldRender = true; },
        enableRangeSelection: function(val) { this.calendar.setEnableRangeSelection(val, true); this.shouldRender = true; },
        hiddenWeekDays: function(val) { this.calendar.setHiddenWeekDays(val, true); this.shouldRender = true; },
        language: function(val) { this.calendar.setLanguage(val, true); this.shouldRender = true; },
        loadingTemplate: function(val) { this.calendar.setLoadingTemplate(val, true); },
        maxDate: function(val) { this.calendar.setMaxDate(val, true); this.shouldRender = true; },
        minDate: function(val) { this.calendar.setMinDate(val, true); this.shouldRender = true; },
        roundRangeLimits: function(val) { this.calendar.setRoundRangeLimits(val, true); this.shouldRender = true; },
        renderStyle: function(val) { this.calendar.setStyle(val, true); this.shouldRender = true; },
        weekStart: function(val) { this.calendar.setWeekStart(val, true); this.shouldRender = true; },
        startDate: function(val) { this.calendar.setStartDate(val); },
        year: function(val) { this.calendar.setYear(val); },
        months: function(val) { this.calendar.setNumberMonthsDisplayed(val); },
        allProps: function(val) {
            if (this.shouldRender) {
                this.calendar.render();
                this.shouldRender = false;
            }
        }
    },
    locales: JsCalendar.locales // Map the "locales" property to the js-year-calendar "locales" property, in order to make the locale files compatible
};
</script>