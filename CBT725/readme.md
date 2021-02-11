```
//***FILE 725 is from Andrew Armstrong and contains his CICS        *   FILE 725
//*           Auxiliary Trace Visualizer, written in REXX.  The     *   FILE 725
//*           following is some documentation about this product.   *   FILE 725
//*                                                                 *   FILE 725
//*     NAME     - AUX2SVG                                          *   FILE 725
//*                                                                 *   FILE 725
//*     TITLE    - CICS AUXILIARY TRACE VISUALIZER                  *   FILE 725
//*                                                                 *   FILE 725
//*     VERSION  - 1.2                                              *   FILE 725
//*                                                                 *   FILE 725
//*     FUNCTION - Creates a graphical representation of a CICS     *   FILE 725
//*                auxilliary trace printout by using Scalable      *   FILE 725
//*                Vector Graphics (SVG).  The SVG markup           *   FILE 725
//*                represents the trace data in the form of a       *   FILE 725
//*                Unified Modelling Language (UML) Sequence        *   FILE 725
//*                Diagram (or at least something quite like        *   FILE 725
//*                it).                                             *   FILE 725
//*                                                                 *   FILE 725
//*                The 'actors' (for example, programs) are         *   FILE 725
//*                listed side- by-side at the top of the           *   FILE 725
//*                diagram. A life line is drawn vertically         *   FILE 725
//*                below each actor. Interactions between actors    *   FILE 725
//*                (for example, calls and returns) are             *   FILE 725
//*                represented as arrows drawn between the life     *   FILE 725
//*                lines.  The vertical axis is time. Each          *   FILE 725
//*                interaction is labeled on the left of the        *   FILE 725
//*                diagram with the relative time in seconds        *   FILE 725
//*                since the start of the trace and the task id.    *   FILE 725
//*                All the interactions for a task are assigned     *   FILE 725
//*                the same unique color. Each interaction is       *   FILE 725
//*                annotated with the trace sequence number, to     *   FILE 725
//*                enable you to refer back to the original         *   FILE 725
//*                trace record for more detail, and a summary      *   FILE 725
//*                of the call and return values. Exception         *   FILE 725
//*                responses are shown in red.                      *   FILE 725
//*                                                                 *   FILE 725
//*                You choose which actors you are interested       *   FILE 725
//*                in by specifying one or more domain names.       *   FILE 725
//*                For example, if you want to visualize TCP/IP     *   FILE 725
//*                socket activity, you might specify the PG        *   FILE 725
//*                (program) and SO (socket) domains:               *   FILE 725
//*                                                                 *   FILE 725
//*                  aux2svg mytrace.txt (PG SO                     *   FILE 725
//*                                                                 *   FILE 725
//*                If you want to examine a storage allocation      *   FILE 725
//*                problem you might specify the SM (storage        *   FILE 725
//*                manager) domain:                                 *   FILE 725
//*                                                                 *   FILE 725
//*                  aux2svg mytrace.txt (SM                        *   FILE 725
//*                                                                 *   FILE 725
//*                By default, ALL domains are selected but this    *   FILE 725
//*                can take a long time to process. It is best      *   FILE 725
//*                to restrict the actors to a few domains that     *   FILE 725
//*                you are interested in.                           *   FILE 725
//*                                                                 *   FILE 725
//*     USAGE    - You can run this Rexx on an IBM mainframe, or    *   FILE 725
//*                on a PC by using Regina Rexx from:               *   FILE 725
//*                                                                 *   FILE 725
//*                   http://regina-rexx.sourceforge.net            *   FILE 725
//*                                                                 *   FILE 725
//*                You can view the resulting SVG file using        *   FILE 725
//*                either:                                          *   FILE 725
//*                                                                 *   FILE 725
//*                1. Microsoft Internet Explorer 6 with the        *   FILE 725
//*                   Adobe SVG Viewer plugin installed. The        *   FILE 725
//*                   plugin is free from www.adobe.com. Open       *   FILE 725
//*                   the html file created by this Rexx if you     *   FILE 725
//*                   want to scroll the output in the browser.     *   FILE 725
//*                   Alternatively, you could publish the html     *   FILE 725
//*                   file on a web server and point your           *   FILE 725
//*                   browser at that web server. Adobe SVG         *   FILE 725
//*                   Viewer supports the following mouse/key       *   FILE 725
//*                   actions:                                      *   FILE 725
//*                                                                 *   FILE 725
//*                   LeftButton+Ctrl           Zoom in             *   FILE 725
//*                   LeftButton+Ctrl+Shift     Zoom out            *   FILE 725
//*                   LeftButton+Alt            Move                *   FILE 725
//*                   LeftButton+Alt+Shift      Move constrained    *   FILE 725
//*                   Tool tips are not supported by this viewer    *   FILE 725
//*                   yet.                                          *   FILE 725
//*                                                                 *   FILE 725
//*                2. Apache Batik Squiggle program with Sun        *   FILE 725
//*                   Java 1.3 or later installed. Batik is free    *   FILE 725
//*                   from www.apache.org  To run Squiggle:         *   FILE 725
//*                   java -jar batik-squiggle.jar                  *   FILE 725
//*                   Squiggle supports the following               *   FILE 725
//*                   mouse/key actions:                            *   FILE 725
//*                                                                 *   FILE 725
//*                   LeftButton+Ctrl (+drag)   Zoom in to rectangle*   FILE 725
//*                   LeftButton+Shift (+drag)  Move                *   FILE 725
//*                   RightButton+Ctrl (+drag)  Rotate              *   FILE 725
//*                   RightButton+Shift (+drag) Zoom (in or out)    *   FILE 725
//*                   Squiggle shows tool tips when you hover       *   FILE 725
//*                   the mouse over items that have a tool tip     *   FILE 725
//*                   defined.                                      *   FILE 725
//*                                                                 *   FILE 725
//*                3. Microsoft Visio 2003 or later.                *   FILE 725
//*                                                                 *   FILE 725
//*                                                                 *   FILE 725
//*     MORE INFO  - See the AUX2SVG rexx procedure for more        *   FILE 725
//*                  information                                    *   FILE 725
//*                                                                 *   FILE 725
//*     NOTES      - 1. The AUX2SVG rexx procedure uses the Rexx    *   FILE 725
//*                     XML parser in CBTTAPE FILE647               *   FILE 725
//*                     (www.cbttape.org).                          *   FILE 725
//*                                                                 *   FILE 725
//*     AUTHOR     - Andrew J. Armstrong                            *   FILE 725
//*                  <andrew_armstrong@unwired.com.au>              *   FILE 725
//*                                                                 *   FILE 725

```
