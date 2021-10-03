# Local-Photo, your lazy-loaded src for images (in React)!

### caches photos with pouchDB under application location storage "react-local-photo"

LICENSE AGPL-3
No redistribution but for strategy of parts, unless retributed

How to use

    import LazyPhoto from "react-local-photo";

    const buttonStyle = {
      borderRadius: "4px",
      backgroundColor: "white",
      color: "black",
      border: "1px solid"
    };
    const make = (fallback, maxWidth, id, i, open) =>
      React.createElement(
        LazyPhoto,
        {
          key: id + i,
          i: i,
          show: (open && i === 0) || (!open && i === 1),
          className: i === 0 ? "eventtypesselected" : "eventtypesnotselected",
          style: { width: "100%" },
          locationPath: `.././Photos/${id}/${i === 0 ? "Open.png" : "Closed.png"}`,
          id,//accessible in parent onClick by e.target.id
          fallback,
          buttonStyle,
          maxWidth,
          nolabel: false,
          verbose: true//false or null for no logging
        },
        id + i
      );
    export class HairNailsTanImg extends React.Component {
      render() {
        const { servtype, tileChosen } = this.props;

        const title = "hair, nails & tan";
        return (
          mount(tileChosen, "servtype") &&
          [
            "https://www.dl.dropboxusercontent.com/s/n7x1nni29yfn3nh/Services_Grooming.png?dl=0", //src
            "https://www.dl.dropboxusercontent.com/s/iis3mgzii9ddtc7/Services_Grooming%20%28closed%29%20%281%29.png?dl=0" //src
          ].map((fallback, i) =>
            make(fallback, null, tileChosen + "/" + title, i, title === servtype)
          )
        );
      }
    }

SEE LICENSE IN LICENSE.lz.txt

copying the src code? https://github.com/npm/cli/issues/3514
npm install --force npm uninstall @babel/polyfill --save ...